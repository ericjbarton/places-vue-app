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

