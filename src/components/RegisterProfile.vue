<template>
<div class="component">
	<h2>Register your profile</h2>
	<div class="form-group">
		<label>Name</label>
		<input type="text" placeholder="Firstname Lastname"
			v-model="profile.name" />
		<!-- <button @click="profile.name = ''">Reset name</button> -->
	</div>

	<div class="form-group">
		<label>Mobile number</label>
		<input type="text" placeholder="(+46) 070-123 456"
			v-model="profile.contactInformation.mobileNumber" />
	</div>

	<div class="form-group">
		<label>Email</label>
		<input type="text" placeholder="example@email.com"
			v-model="profile.contactInformation.eMailAddress" />
	</div>

	<div class="form-group">
		<label>Photo URL</label>
		<input type="text" placeholder="https://path.to/image.jpeg"
			v-model="profile.photo" />
	</div>

	{{ profile }}
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
		}
	})
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
.form-group label, .form-group input { display: block; }
.form-group input {
	width: 20em;
}





</style>
