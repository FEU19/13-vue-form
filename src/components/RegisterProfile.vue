<template>
<div class="component">
	<h2>Register your profile</h2>
	<div class="form-group">
		<label>Name</label>
		<input type="text" placeholder="Firstname Lastname"
			v-model="profile.name" :class="nameClass"
			@blur.once="nameIsTouched = true" />
		<!-- <button @click="profile.name = ''">Reset name</button> -->
		<span v-if="nameIsTouched && !nameIsValid" class="error"> {{ nameErrorMessage }} </span>
	</div>

	<div class="form-group">
		<label>Mobile number</label>
		<input type="text" placeholder="(+46) 070-123 456"
			v-model="profile.contactInformation.mobileNumber"
			:class="mobileClass" @blur.once="mobileIsTouched = true" />
		<span v-if="mobileIsTouched && !mobileIsValid" class="error"> {{ mobileErrorMessage }}</span>
	</div>

	<div class="form-group">
		<label>Email</label>
		<input type="text" placeholder="example@email.com"
			v-model="profile.contactInformation.eMailAddress"
			:class="emailClass" @blur.once="emailIsTouched = true" />
		<span v-if="emailIsTouched && !emailIsValid" class="error"> {{ emailErrorMessage }}</span>
	</div>

	<div class="form-group">
		<label>Photo URL</label>
		<input type="text" placeholder="https://path.to/image.jpeg"
			v-model="profile.photo" :class="photoClass" @blur.once="photoIsTouched = true" />
		<span v-if="photoIsTouched && !photoIsValid" class="error"> {{ photoErrorMessage }}</span>
	</div>

	<div class="form-group">
		<label>Education and courses</label>
		<input type="text" placeholder="Name of school or course"
			v-model="inputEducation" :class="educationClass" />
		<button @click="profile.education.push(inputEducation); inputEducation = '';"
			:disabled="educationExist">Save education</button>
		<div class="list">
			<div v-for="edu in profile.education" :key="edu">
				<span> {{ edu }} </span>
				<button @click="removeEducation(edu)">Remove</button>
			</div>
		</div>
	</div>

	<button :disabled="!formIsValid" class="submit">Next step</button>

	<!-- {{ profile }} -->
</div>
</template>

<script>
export default {
	data: () => ({
		profile: {
			name: '',
			contactInformation: {
				mobileNumber: '(+46) 070-123 456',
				eMailAddress: 'example@email.com'
			},
			photo: '',  // bör inte vara obligatoriskt
			city: '',  // valfri
			education: [],  // utbildning kan vara relevant för att söka ett jobb
			jobSkills: [],  // relevant kompetens, namn på tekniker
			experiences: [],
			ageRequirementNeedsBetterName: '',  // kan vara viktig i vissa fall - över 18 för vissa jobb - valfri - kanske checkbox?
			interestedIn: '',  // valfri
			jobType: ''  // heltid, deltid eller timmar
		},
		inputEducation: '',  // det som användaren skriver i input-fältet
		nameIsTouched: false,
		mobileIsTouched: false,
		emailIsTouched: false,
		photoIsTouched: false
	}),
	computed: {
		nameIsValid() {
			return this.profile.name.length >= 2;
			// if( this.profile.name.length >= 2 )
			// 	return true;
			// else
			// 	return false;
		},
		nameClass() {
			if( !this.nameIsTouched ) return '';
			return this.nameIsValid ? 'valid' : 'invalid';
		},
		nameErrorMessage() {
			return 'Please enter at least two characters.'
		},

		mobileIsValid() {
			// If we want to validate with more precision, consider regular expressions.
			return this.profile.contactInformation.mobileNumber.length >= 10;
		},
		mobileClass() {
			if( !this.mobileIsTouched ) return '';
			return this.mobileIsValid ? 'valid' : 'invalid';
		},
		mobileErrorMessage() {
			return 'Your mobile number should have 10 characters';
		},

		emailIsValid() {
			const email = this.profile.contactInformation.eMailAddress;
			return email.length > 0 && email.includes('@');
		},
		emailClass() {
			if( !this.emailIsTouched ) return '';
			return this.emailIsValid ? 'valid' : 'invalid';
		},
		emailErrorMessage() {
			return 'Please enter a valid email address';
		},

		photoIsValid() {
			const photo = this.profile.photo.toLowerCase();
			const correctEnding = photo.endsWith('png') || photo.endsWith('jpg') || photo.endsWith('jpeg');
			return photo == '' || (photo.startsWith('https://') && correctEnding);
		},
		photoClass() {
			if( !this.photoIsTouched ) return '';
			return this.photoIsValid ? 'valid' : 'invalid';
			// if( this.photoIsValid ) return 'valid'; else return 'invalid';
		},
		photoErrorMessage() {
			return 'Please enter a valid URL'
		},

		educationExist() {
			// Kontrollera om inputEducation finns i listan profile.education
			return this.profile.education.find(
				edu => edu.toLowerCase() == this.inputEducation.toLowerCase()
			);
			// object -> true
			// undefined -> false
		},
		educationClass() {
			return this.educationExist ? 'invalid' : '';
		},

		formIsValid() {
			return this.nameIsValid && this.mobileIsValid && this.emailIsValid && this.photoIsValid;
		}
	},
	methods: {
		removeEducation(education) {
			this.profile.education = this.profile.education.filter(
				edu => edu != education
			);
		}
	}
}
</script>

<style scoped>
.component {
	border: 1px solid gray;
	border-radius: 1em;
	padding: 1em;
	margin: 1em;
}

.form-group {
	border: 1px solid lightgray;
	border-radius: 0.3em;
	padding: 0.3em;
	margin: 0.3em;
}
.form-group label { display: block; }
.form-group input {
	width: 20em;
}

input.valid { border-color: green; }
input.invalid { border-color: red; }
.error {
	color: red;
	font-size: 90%;
}

.list > div {
	display: flex;
	justify-content: space-between;
	width: 20em;
	border: 1px solid lightgray;
}
.list > div:hover {
	background-color: beige;
}
button.submit {
	font-size: 1.1em;
	padding: 0.5em 1em;
}
button.submit:disabled {
	background-color: white;
	color: lightgray;
}


</style>
