<template>
  <q-page class="flex flex-center">
    <img alt="Quasar logo" src="../assets/logo.png">
    <q-btn dense flat round icon="aspect_ratio" @click="setFullScreen"/>
  </q-page>
</template>

<style>
</style>

<script>
export default {
  name: 'HelloWorld',
  methods: {
    setFullScreen: function () {
      const electron = require('electron');
      const net = electron.remote.net;
      const request = net.request({
        method: 'GET',
        protocol: 'http:',
        hostname: 'cas.hdu.edu.cn',
        path: '/cas/login?service=http://jxgl.hdu.edu.cn/default.aspx'
      });
      request.on('response', (response) => {
        console.log(`STATUS: ${response.statusCode}`);
        console.log(response.headers);
      });
      request.on('finish', () => {
        console.log('Request is Finished')
      });
      request.on('abort', () => {
        console.log('Request is Aborted')
      });
      request.on('error', (error) => {
        console.log(`ERROR: ${JSON.stringify(error)}`)
      });
      request.on('close', (error) => {
        console.log(`Last Transaction has occured: ${JSON.stringify(error)}`)
      });
      request.setHeader('Content-Type', 'application/json');
      request.end();
    }
  }
}
</script>
