<template>
  <div class="school-list">
    <input
      v-model="searchQuery"
      @input="debouncedFetchSchools"
      placeholder="Search campaign here"
      type="text"
    />
    <div v-if="error" class="error">{{ error }}</div>
    <div v-if="schools.length">
      <li v-for="school in schools" :key="school.id" class="school-item">
        <div class="flex-rw">
            <img :src="school.logo_url" alt="School Logo" class="school-logo" />
            <div class="school-details">
              {{ school.school_name }}
            </div>
        </div>
        <div v-if="school.campaign_detail">
            <button class="join-btn" @click="joinCampaign(school.id)">Join campaign</button>
        </div>
      </li>
    </div>
    <div v-else>
      <p>No campaigns found.</p>
    </div>
    <div v-if="showPopup">
       
    </div>
    <SmallPopupModal v-if="showPopup" :title="'Campaign Details'" @close="closePopup">
        <CampaignDetailPopup
            :campaign-details="campaignDetails"
        />
      </SmallPopupModal>
  </div>
</template>

<script>
import axios from "axios";
import { debounce } from "lodash";
import CampaignDetailPopup from '../components/CampaignDetailPopup'
import SmallPopupModal from '../components/SmallPopupModal.vue'
  
export default {
    components: {
        CampaignDetailPopup,
        SmallPopupModal
    },
  data() {
    return {
      schools: [],
      searchQuery: "",
      error: null,
      campaignDetails: [],
      showPopup: false
    };
  },
  methods: {
    async fetchSchools() {
      try {
        // Base API URL
        let apiUrl =
          "http://api.devharlemwizardsinabox.com/campaign/campaign_school_list/";
        if (this.searchQuery.trim()) {
          apiUrl += `?search=${this.searchQuery}`;
        }
        const response = await axios.get(apiUrl);
        if (response.data.success) {
          this.schools = response.data.school_list || [];
          this.error = null;
        } else {
          this.schools = [];
          this.error = "Failed to retrieve school data.";
        }
      } catch (error) {
        this.schools = [];
        this.error = "Error loading school data. Please try again later.";
      }
    },
      debouncedFetchSchools: debounce(function () {
      this.fetchSchools();
    }, 500),
    joinCampaign (id) {
        this.showPopup = true
        if (this.schools) {
            this.schools.forEach((item, index) => {
                if (item.id === id) {
                    console.log(this.schools[index].campaign_detail)
                    this.campaignDetails = this.schools[index].campaign_detail
                }
            })
        }
    },
    closePopup () {
        this.showPopup = false
    }
  },
  mounted() {
    this.fetchSchools();
  },
};
</script>
  
<style scoped lang="scss">
@import '../styles.scss'; 
.school-list {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
}

input {
  width: 95%;
  padding: 12px 20px;
  margin-bottom: 20px;
  border: 1px solid #ccc;
  border-radius: 10px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  font-size: 16px;
  outline: none;
  transition: box-shadow 0.3s ease-in-out;
}

input:focus {
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

.error {
  color: red;
}

.school-item {
  display: flex;
  align-items: center;
  justify-content: space-between;
  background-color: #f6f6f6;
  border-radius: 7px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  margin-bottom: 20px;
  padding: 10px 20px;
  transition: transform 0.2s ease-in-out;
  gap: 5rem;
  width: 95%;
}
  
  .school-item:hover {
    transform: translateY(-5px);
    box-shadow: 0 6px 12px rgba(0, 0, 0, 0.15);
  }
  
  .school-logo {
    width: 30px;
    height: 30px;
    margin-right: 5px;
    object-fit: cover;
    border-radius: 10px;
  }
  
  .school-details {
    margin: 0;
    font-size: 1rem;
    font-weight: 600;
  }
  
  .school-details p {
    margin: 5px 0;
    font-size: 1rem;
    color: #555;
  }

  .flex-rw {
    align-items: center;
  }

  .join-btn {
    color: $primary-color;
    border: 1px solid $primary-color;
    border-radius: 10px;
    font-weight: 600;
    background-color: #fff;
    padding: 5px 10px;
    &:hover {
        cursor: pointer;
    }
  }
  </style>
  