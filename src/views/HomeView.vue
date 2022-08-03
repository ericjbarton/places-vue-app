<script>
import axios from "axios";
export default {
  data: function () {
    return {
      message: "Paper Towns",
      places: [],
      editPlaceParams: {},
      newPlaceParams: {},
      showErrorMessage: false,
      errorMessage: "",
      
    };
  },

  created: function () {
    this.indexPlaces();
  },
  methods: {
    indexPlaces: function () {
      axios.get("http://localhost:3000/places").then((response) => {
        this.places = response.data;
        console.log("All Phantom Towns", this.places);
      });
    },
      showPlace: function (place) {
      console.log(place);
      document.querySelector("#place-details").showModal();
      this.currentPlace = place;
      this.editPlaceParams = place;
      },
        
        createPlace: function () {
      axios
        .post("http://localhost:3000/places", this.newPlaceParams)
        .then((response) => {
          console.log("Paper Town created", response.data);
          this.places.push(response.data);
          this.newPlaceParams = {}; 
          this.showErrorMessage = false;
        })
        .catch((error) => (this.errorMessage = error))
        .then((this.showErrorMessage = true));
        },
        
        updatePlace: function () {
          axios
          .patch("http://localhost:3000/places" + place.id)
        }