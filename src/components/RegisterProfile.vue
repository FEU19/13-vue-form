<template>
<div class="component">
	<h2>Register your profile</h2>
	<div class="form-group">
		<label>label</label>
		<input type="text" placeholder="exempel" />
	</div>

	<div class="form-group">
		<label>label</label>
		<input type="text" placeholder="exempel" />
	</div>

	<div class="form-group">
		<label>label</label>
		<input type="text" placeholder="exempel" />
	</div>

	<div class="form-group">
		<label>label</label>
		<input type="text" placeholder="exempel" />
	</div>

</div>
</template>

<script>
export default {
	data: () => ({
		profile: {
			name: '',
			education: [],  // utbildning kan vara relevant för att söka ett jobb
			jobSkills: [],  // relevant kompetens, namn på tekniker
			experiences: [],
			contactInformation: {
				mobileNumber: '(+46) 070-123 456',
				eMailAddress: 'example@email.com'
			},
			photo: '',  // bör inte vara obligatoriskt
			city: '',  // valfri
			ageRequirement: '',  // kan vara viktig i vissa fall - över 18 för vissa jobb - valfri - kanske checkbox?
			interestedIn: '',  // valfri
			jobType: ''  // heltid, deltid eller timmar
		}
	})
}
</script>

<style scoped>









</style>
