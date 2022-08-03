<script>
import axios from "axios";
export default {
  data: function () {
    return {
      places: [],
      editPlaceParams: {},
      newPlaceParams: {},
      
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
        createPlace: function () {
      axios
        .post("http://localhost:3000/places", this.newPlaceParams)
        .then((response) => {
          console.log("Place created ", response.data);
          this.places.push(response.data);
          this.newPlaceParams = {};
          this.showErrorMessage = false;
        
