<template>
<div class= "">
	<h1 style text-align="center">Prvi page</h1>
	<v-data-table
	:headers="headers"
	:name="imeknjige"
	:authors="pautor"
	:relesed="datumizdavanja">
	<template v-slot:item.website="{item}">
		<a :href="item.airline.website">{{item.airline.website}}</a>
		</template>
	</v-data-table>
</div>
</template>

<script>
import axios from "axios";
export default {
	name:"datakomponent",
	data(){
		return{
			imeknjige:"",
			pauthor: "",
			datumizdavanja: "",
			headers: [
				{text: "Ime knjige", value:"Ime_knjige"},
				{text: "Prvi autor", value:"Prvi_autor"},
				{text: "datum idzavanja", value:"Datum"}
			],
		};
	},
	//pracenje podataka kad korisnik promjeni trenutni page
watch: {
	options: {
		handler(){
			this.readDataFromAPI();
		},
	},
	deep: true,
},
	methods: {
		readDataFromAPI(){
			this.loading = true;
			const {page, itemsPerPage}=this.options;
			let pagenumber = page -1;
			axios
				.get("https://www.anapioficeandfire.com/api/books" + itemsPerPage + "$page= "+ pagenumber
				)
				.then ((response)=>{
					this.loading = false;
					this.
				})
		}
}
};
</script>


<style scoped>
</style>
