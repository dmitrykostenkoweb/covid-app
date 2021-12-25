<template>
  <section class="section">
    <div class="section__wrapper">
      <label for="country"
        >Hi 👋, I will help you choose a country! Just start typing the country
        name.
      </label>

      <input
        id="country"
        v-model="country"
        type="text"
        autocomplete="off"
        @input="autocomplete"
      />
      <div class="autocomplete-list__wrapper">
        <div class="autocomplete-list">
          <li
            v-for="item in option"
            :key="item"
            class="autocomplete-list__item"
            @click="selected(item)"
            v-on:keyup.down="selected(item)"
          >
            {{ item }}
          </li>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'AppBar',
  components: {},
  data() {
    return {
      country: '',
      optionsArr: [
        'Afghanistan',
        'Albania',
        'Algeria',
        'Andorra',
        'Angola',
        'Anguilla',
        'Antigua & Barbuda',
        'Argentina',
        'Armenia',
        'Aruba',
        'Australia',
        'Austria',
        'Azerbaijan',
        'Bahamas',
        'Bahrain',
        'Bangladesh',
        'Barbados',
        'Belarus',
        'Belgium',
        'Belize',
        'Benin',
        'Bermuda',
        'Bhutan',
        'Bolivia',
        'Bosnia & Herzegovina',
        'Botswana',
        'Brazil',
        'British Virgin Islands',
        'Brunei',
        'Bulgaria',
        'Burkina Faso',
        'Burundi',
        'Cambodia',
        'Cameroon',
        'Canada',
        'Cape Verde',
        'Cayman Islands',
        'Central Arfrican Republic',
        'Chad',
        'Chile',
        'China',
        'Colombia',
        'Congo',
        'Cook Islands',
        'Costa Rica',
        'Cote D Ivoire',
        'Croatia',
        'Cuba',
        'Curacao',
        'Cyprus',
        'Czech Republic',
        'Denmark',
        'Djibouti',
        'Dominica',
        'Dominican Republic',
        'Ecuador',
        'Egypt',
        'El Salvador',
        'Equatorial Guinea',
        'Eritrea',
        'Estonia',
        'Ethiopia',
        'Falkland Islands',
        'Faroe Islands',
        'Fiji',
        'Finland',
        'France',
        'French Polynesia',
        'French West Indies',
        'Gabon',
        'Gambia',
        'Georgia',
        'Germany',
        'Ghana',
        'Gibraltar',
        'Greece',
        'Greenland',
        'Grenada',
        'Guam',
        'Guatemala',
        'Guernsey',
        'Guinea',
        'Guinea Bissau',
        'Guyana',
        'Haiti',
        'Honduras',
        'Hong Kong',
        'Hungary',
        'Iceland',
        'India',
        'Indonesia',
        'Iran',
        'Iraq',
        'Ireland',
        'Isle of Man',
        'Israel',
        'Italy',
        'Jamaica',
        'Japan',
        'Jersey',
        'Jordan',
        'Kazakhstan',
        'Kenya',
        'Kiribati',
        'Kosovo',
        'Kuwait',
        'Kyrgyzstan',
        'Laos',
        'Latvia',
        'Lebanon',
        'Lesotho',
        'Liberia',
        'Libya',
        'Liechtenstein',
        'Lithuania',
        'Luxembourg',
        'Macau',
        'Macedonia',
        'Madagascar',
        'Malawi',
        'Malaysia',
        'Maldives',
        'Mali',
        'Malta',
        'Marshall Islands',
        'Mauritania',
        'Mauritius',
        'Mexico',
        'Micronesia',
        'Moldova',
        'Monaco',
        'Mongolia',
        'Montenegro',
        'Montserrat',
        'Morocco',
        'Mozambique',
        'Myanmar',
        'Namibia',
        'Nauro',
        'Nepal',
        'Netherlands',
        'Netherlands Antilles',
        'New Caledonia',
        'New Zealand',
        'Nicaragua',
        'Niger',
        'Nigeria',
        'North Korea',
        'Norway',
        'Oman',
        'Pakistan',
        'Palau',
        'Palestine',
        'Panama',
        'Papua New Guinea',
        'Paraguay',
        'Peru',
        'Philippines',
        'Poland',
        'Portugal',
        'Puerto Rico',
        'Qatar',
        'Reunion',
        'Romania',
        'Russia',
        'Rwanda',
        'Saint Pierre & Miquelon',
        'Samoa',
        'San Marino',
        'Sao Tome and Principe',
        'Saudi Arabia',
        'Senegal',
        'Serbia',
        'Seychelles',
        'Sierra Leone',
        'Singapore',
        'Slovakia',
        'Slovenia',
        'Solomon Islands',
        'Somalia',
        'South Africa',
        'South Korea',
        'South Sudan',
        'Spain',
        'Sri Lanka',
        'St Kitts & Nevis',
        'St Lucia',
        'St Vincent',
        'Sudan',
        'Suriname',
        'Swaziland',
        'Sweden',
        'Switzerland',
        'Syria',
        'Taiwan',
        'Tajikistan',
        'Tanzania',
        'Thailand',
        "Timor L'Este",
        'Togo',
        'Tonga',
        'Trinidad & Tobago',
        'Tunisia',
        'Turkey',
        'Turkmenistan',
        'Turks & Caicos',
        'Tuvalu',
        'Uganda',
        'Ukraine',
        'United Arab Emirates',
        'United Kingdom',
        'United States of America',
        'Uruguay',
        'Uzbekistan',
        'Vanuatu',
        'Vatican City',
        'Venezuela',
        'Vietnam',
        'Virgin Islands (US)',
        'Yemen',
        'Zambia',
        'Zimbabwe',
      ],
      option: [],
    }
  },
  // props: {
  //   dialog: {
  //     type: String,
  //     require: true,
  //   },
  // },
  methods: {
    selected(select) {
      this.country = select
      this.$emit('selectedCountry', this.country)
      this.option = []
      this.country = ''
    },
    autocomplete() {
      if (this.country) {
        this.option = this.optionsArr.filter((opt) =>
          opt.toLowerCase().includes(this.country)
        )

        const numberOfOptions = 5
        if (this.option.length > numberOfOptions) {
          this.option.splice(
            numberOfOptions,
            this.option.length - numberOfOptions
          )
        }
        if (this.option.length === 1) {
          this.selected(this.option[0])
        }
      }
      if (!this.country) {
        this.option = []
      }
    },
  },
}
</script>

<style scoped>
.section__wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-around;
  flex-wrap: wrap;
}

.autocomplete-list__wrapper {
  position: relative;
  width: 200px;
}
.autocomplete-list {
  position: absolute;
  top: 0;
  left: 0;
}

.autocomplete-list__item {
  width: 200px;
  list-style: none;
  padding: 5px 10px;
  background-color: rgba(255, 255, 255, 0.8);
  cursor: pointer;
  color: black;
}
.autocomplete-list__item :hover {
  background-color: rgba(151, 151, 151, 0.8);
}
</style>
