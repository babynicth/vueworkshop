<template>
  <div id="faculty" class="tmp">
    <p>facultly : {{ fac }}</p>
    <p>{{ bc }}</p>
    <p>1. สาขาวิชาเทคโนโลยีสารสนเทศ</p>
    <p>2. สาขาวิชาวิทยาการคอมพิวเตอร์</p>
    <p>3. สาขาวิชาวิทยาศาสตร์สิ่งแวดล้อม</p>
    <p>4. สาขาวิชาเคมี</p>
    <p>5. สาขาวิชาคณิตศาสตร์ประยุกต์</p>
    <p>6. สาขาวิชาฟิสิกส์</p>
  </div>
</template>

<script>
export default {
  name: "faculty",
  data() {
    return {
      fac: "คณะวิทยาศาสตร์",
      bc: "มี 6 สาขาดังนี้",
    };
  },
};
</script>

<style>
.tmp {
  font-size: 15 em;
}
#facultly {
  background-color: lightblue;
  color: black;
}
</style>