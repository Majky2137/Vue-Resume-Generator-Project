<script>
export default {
  name: 'FormRes',
  data () {
    return {
      BirthDay: '',
      url: null,
      FirstName: '',
      LastName: '',
      About: '',
      Selected: '',
      Skills: [
        { id: '1', value: 'Vue' },
        { id: '2', value: 'React' },
        { id: '3', value: 'PHP' },
        { id: '4', value: 'Application Development'},
        { id: '5',  value: 'UX Design'},
        { id: '6',  value: 'JavaScript'},
      ],
    }
  },
  methods: {
    onFileChange (e) {
      const file = e.target.files[0]
      this.url = URL.createObjectURL(file)
    }
  }
}
</script>
<template>
  <div class="wrapper">
    <div class="form_left">
      <form class="form_container" action="" method="">
        <p>First name:</p>
        <input
          v-model="FirstName"
          name="FirstName"
          class="text_input"
          placeholder="First name"
          autofocus="autofocus"
          type="text"
          required="required"
        />
        <p>Last name</p>
        <input
          v-model="LastName"
          name="LastName"
          class="text_input"
          placeholder="Last name"
          type="text"
          required="required"
        />
        <p>Birthday</p>
        <input
          v-model="BirthDay"
          name="BirthDay"
          class="text_input"
          placeholder="Your Birth Day"
          type="date"
          min="1997-01-01"
          max="2030-12-31"
          required="required"
        />
        <p>Image</p>
        <input type="file" @change="onFileChange" class="text_input" />
        <p>Experience</p>
        <textarea
          v-model="About"
          name="about"
          class="text_area_input"
          type="text"
          placeholder="Tell something about yourself"
          required="required"
        />

        <p>Skills</p>
        <select class="select_input" name="Skills"  v-model="Selected" multiple>
        <option v-for="Skill in Skills" :value="Skill.value" :key="Skill.id">
          {{ Skill.value }}
       </option>
        </select>
      </form>
    </div>
    <div class="preview_container">
      <div class="resume_header">
        <div class="resume_left_header">
          <div class="img_container">
            <img v-if="url" :src="url" />
          </div>
        </div>
        <div class="resume_right_header">
          <div class="left">
            <p>Date of birth:</p>
            <span>{{ BirthDay }}</span>

            <h1>{{ FirstName }}</h1>
            <h1>{{ LastName }}</h1>
          </div>
          <div class="right">
            <p>Short description</p>
            <span style="white-space: pre-line;">{{ About }}</span>
          </div>
        </div>
      </div>
      <div class="main">
        <div class="left_main_container">
          <div class="cont_info">
          <div class="section_headings">
            <h2>Skills</h2>
          </div>
          <span>{{Selected}}</span>
          </div>
          <div class="cont_info">
          <div class="section_headings">
            <h3>Additional skills</h3>
          </div>
        </div>

        <div class="cont_info">
          <div class="section_headings">
            <h3>Interest</h3>
          </div>
          </div>

          <div class="cont_info">
          <div class="section_headings">
            <h3>Languages</h3>
          </div>
          </div>

        </div>
        <div class="right_main_container"></div>
      </div>
    </div>
  </div>
</template>


<style scoped>
html,
body {
  width: 100%;
  height: 100%;
}
.wrapper {
  position: relative;
  display: flex;
  flex-direction: row;
  width: 100%;
  height: 120vh;
  overflow-x: hidden;
  margin: 0;
}
.form_left {
  position: relative;
  display: flex;
  width: 50%;
  height: 100%;
  border-right: 1px solid rgb(27, 27, 27);
}
.preview_container {
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;

  width: 50%;
  height: 100%;
}
.main {
  position: relative;
  display: flex;
  flex-direction: row;
  width: 100%;
  height: 100%;
}
.main > .right_main_container {
  position: relative;
  display: flex;
  width: 60%;
  height: 100%;
  background-color: #e3e3e3;
}
.left_main_container > .cont_info {
  position: relative;
  display: flex;
  flex-direction: column;
  width: 100%;
  padding: 20px;
  max-height: calc(10vh);
}
.left_main_container > .section_headings {
  position: relative;
  display: flex;
  width: 100%;
  padding: 20px;
  max-height: calc(10vh);
}
.main > .left_main_container {
  display: flex;
  position: relative;
  flex-direction: column;
  width: 40%;
  height: 100%;
  background-color: #e3e3e3;
}
.preview_container > .resume_header {
  position: relative;
  display: flex;
  flex-direction: row;
  background-color: #42b983;
  width: 100%;
  height: calc(auto);
}
.preview_container > .resume_header > .resume_left_header {
  position: relative;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  padding: 20px;
  width: 20%;
}
.preview_container > .resume_header > .resume_right_header {
  position: relative;
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  align-items: center;
  padding: 20px;
  width: 90%;
}
.preview_container > .resume_header > .resume_right_header > .left {
  position: relative;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: baseline;
  height: 100%;
  margin-right: 30px;
  max-width: 50%;
}
.preview_container > .resume_header > .resume_right_header > .right {
  position: relative;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: baseline;
  height: 100%;
  max-width: 50%;
}
.preview_container > .resume_header > .resume_right_header > .right > span {
  resize: none;
  box-shadow: none;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  width: 100%;
  overflow: hidden;
  text-overflow: ellipsis;
  font-size: 16px;
  max-height: calc(18vh);
  min-height: calc(18vh);
  max-width: 100%;
  color: #e3e3e3;
  text-align: left;
  position: relative;
}

.preview_container > .resume_header > .resume_right_header > .left > h1 {
  resize: none;
  display: flex;
  box-shadow: none;
  display: flex;
  width: 50%;
  margin: 0;
  font-size: 22px;
  color: #e3e3e3;
  position: relative;
}
.preview_container > .resume_header > .resume_right_header > .left > span {
  resize: none;
  box-shadow: none;
  display: flex;
  width: 100%;
  font-size: 16px;
  margin: 0;
  color: #e3e3e3;
  position: relative;
}

.preview_container > .resume_header > .resume_left_header > .img_container {
  position: relative;
  display: flex;
  margin-right: 8px;
  max-height: calc(19vh);
  width: 100%;
  background-color: #e3e3e3;
  content: "UPLOAD";
  object-fit: cover;
}
.preview_container
  > .resume_header
  > .resume_left_header
  > .img_container
  > img {
  position: relative;
  display: flex;
  height: 100%;
  width: 100%;
  object-fit: cover;
}
.form_container {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
  height: 100%;
}
.form_container > p {
  display: flex;

  align-items: center;
  width: 50%;
}
.text_input {

  box-shadow: none;
  display: flex;
  width: 50%;
  height: 24px;
  padding: 6px 12px;
  font-size: 14px;
  line-height: 1.42857143;
  color: #555;
  background-color: #fff;
  border: 1px solid #ccc;
  position: relative;
  border-radius: 4px;
  transition: border-color ease-in-out 0.15s, box-shadow ease-in-out 0.15s;
  transition-property: border-color, box-shadow;
  transition-duration: 0.15s, 0.15s;
  transition-timing-function: ease-in-out, ease-in-out;
  transition-delay: 0s, 0s;
}
.select_input {
  resize: none;
  box-shadow: none;
  max-height: 80px;
  width: 50%;
  padding: 6px 12px;
  font-size: 14px;
  color: #555;
  background-color: #fff;
  border: 1px solid #ccc;
  border-radius: 4px;
  transition: border-color ease-in-out 0.15s, box-shadow ease-in-out 0.15s;
  transition-property: border-color, box-shadow;
  transition-duration: 0.15s, 0.15s;
  transition-timing-function: ease-in-out, ease-in-out;
  transition-delay: 0s, 0s;
}

input [type="file"] {
  color: green;
}
.text_area_input {
  resize: none;
  box-shadow: none;
  display: flex;
  text-align: left;
  width: 50%;
  height: 80px;
  padding: 6px 12px;
  font-size: 14px;
  line-height: 1.42857143;
  color: #555;
  background-color: #fff;
  border: 1px solid #ccc;
  position: relative;
  border-radius: 4px;
  transition: border-color ease-in-out 0.15s, box-shadow ease-in-out 0.15s;
  transition-property: border-color, box-shadow;
  transition-duration: 0.15s, 0.15s;
  transition-timing-function: ease-in-out, ease-in-out;
  transition-delay: 0s, 0s;
}
@media screen and (max-width: 960px) {
  .wrapper {
    flex-direction: column;
  }
  .resume_header {
    max-height: 20vh;
  }
  .preview_container > .resume_header > .resume_left_header {
    padding: 10px;
    width: 20%;
  }
  .preview_container > .resume_header > .resume_right_header {
    padding: 10px;
    width: 95%;
  }
  .preview_container > .resume_header > .resume_right_header > .left > h1 {
    font-size: 15px;
  }
  .form_left {
    width: 100%;
    margin-bottom: 40px;
  }
  .preview_container {
    width: 100%;
  }
  .preview_container > .resume_header > .resume_right_header > .right > span {
    margin-right: 30px;
    font-size: 12px;
    min-height: calc(10vh);
    max-height: calc(10vh);
  }
  .preview_container > .resume_header > .resume_left_header > .img_container {
    max-height: 22vh;
    max-width: 16vw;
  }
}
</style>
