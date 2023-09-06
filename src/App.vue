

<template>
  <div class="flex-1 p:2 sm:p-6 justify-between flex flex-col h-screen">
    <div class="flex sm:items-center justify-between py-3 border-b-2 border-gray-200">
      <div class="relative flex items-center space-x-4">
         <div class="relative">
            <span class="absolute text-green-500 right-0 bottom-0">
               <svg width="20" height="20">
                  <circle cx="8" cy="8" r="8" fill="currentColor"></circle>
               </svg>
            </span>
         <img src="https://explore.danangairportterminal.vn/wp-content/uploads/2023/08/home-slider.jpg" alt="" class="w-10 sm:w-16 h-10 sm:h-16 rounded-full">
         </div>
         <div class="flex flex-col leading-tight">
            <div class="text-2xl mt-1 flex items-center">
               <span class="text-gray-700 mr-3">Da Nang</span>
            </div>
            <span class="text-lg text-gray-600">International Terminal</span>
         </div>
      </div>
      <!-- <div class="flex items-center space-x-2">
         <button type="button" class="inline-flex items-center justify-center rounded-lg border h-10 w-10 transition duration-500 ease-in-out text-gray-500 hover:bg-gray-300 focus:outline-none">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" class="h-6 w-6">
               <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"></path>
            </svg>
         </button>
         <button type="button" class="inline-flex items-center justify-center rounded-lg border h-10 w-10 transition duration-500 ease-in-out text-gray-500 hover:bg-gray-300 focus:outline-none">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" class="h-6 w-6">
               <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4.318 6.318a4.5 4.5 0 000 6.364L12 20.364l7.682-7.682a4.5 4.5 0 00-6.364-6.364L12 7.636l-1.318-1.318a4.5 4.5 0 00-6.364 0z"></path>
            </svg>
         </button>
         <button type="button" class="inline-flex items-center justify-center rounded-lg border h-10 w-10 transition duration-500 ease-in-out text-gray-500 hover:bg-gray-300 focus:outline-none">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" class="h-6 w-6">
               <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 17h5l-1.405-1.405A2.032 2.032 0 0118 14.158V11a6.002 6.002 0 00-4-5.659V5a2 2 0 10-4 0v.341C7.67 6.165 6 8.388 6 11v3.159c0 .538-.214 1.055-.595 1.436L4 17h5m6 0v1a3 3 0 11-6 0v-1m6 0H9"></path>
            </svg>
         </button>
      </div> -->
   </div>
   <div v-bind:class="{ishiden : active}">
        <div style="text-align: center;">
          <h3 class=" font-bold">Please Input Your Name !</h3>
          <input v-bind:class="{ishiden : active , 'inname': !active}" @keyup.enter="submit" v-model="user" placeholder="UserName" />
        </div>
    </div>
    <!-- Nội dung hội thoại -->
    <div id="messages" class="flex flex-col space-y-4 p-3 overflow-y-auto scrollbar-thumb-blue scrollbar-thumb-rounded scrollbar-track-blue-lighter scrollbar-w-2 scrolling-touch">
    <div v-for="(message, index) in messages" :key="index">
      <div class="chat-message" v-if="message.user != userActual">
         <div class="flex items-end">
            <div class="flex flex-col space-y-2 text-xs max-w-xs mx-2 order-2 items-start">
               <div><span class="px-4 py-2 rounded-lg inline-block bg-gray-300 text-gray-600">{{ message.message }}</span></div>
               <!-- <div>
                  <span class="px-4 py-2 rounded-lg inline-block rounded-bl-none bg-gray-300 text-gray-600">
                     Check the line above (it ends with a # so, I'm running it as root )
                     <pre># npm install -g @vue/devtools</pre>
                  </span>
               </div> -->
            </div>
            <img src="https://images.unsplash.com/photo-1549078642-b2ba4bda0cdb?ixlib=rb-1.2.1&amp;ixid=eyJhcHBfaWQiOjEyMDd9&amp;auto=format&amp;fit=facearea&amp;facepad=3&amp;w=144&amp;h=144" alt="My profile" class="w-6 h-6 rounded-full order-1">
         </div>
      </div>
      <div class="chat-message" v-else>
         <div class="flex items-end justify-end">
            <div class="flex flex-col space-y-2 text-xs max-w-xs mx-2 order-1 items-end">
               <div><span class="px-4 py-2 rounded-lg inline-block rounded-br-none bg-blue-600 text-white ">{{ message.message }}</span></div>
            </div>
            <img src="https://images.unsplash.com/photo-1590031905470-a1a1feacbb0b?ixlib=rb-1.2.1&amp;ixid=eyJhcHBfaWQiOjEyMDd9&amp;auto=format&amp;fit=facearea&amp;facepad=3&amp;w=144&amp;h=144" alt="My profile" class="w-6 h-6 rounded-full order-2">
         </div>
      </div>
    </div>
      
   </div>


   <!-- //<HelloWorld msg="Vite + Vue" /> -->
   <p v-if="connectionState === 'Connecting'">Connecting...</p>
    <p v-else-if="connectionState === 'Connected'">Connected.</p>
    <p v-else-if="connectionState === 'Reconnecting'">Reconnecting...</p>
    <p v-else-if="connectionState === 'Disconnected'">Disconnected.</p>
   <div class="border-t-2 border-gray-200 px-4 pt-4 mb-2 sm:mb-0">
      <div class="relative flex">
         <span class="absolute inset-y-0 flex items-center">
            <button type="button" class="inline-flex items-center justify-center rounded-full h-12 w-12 transition duration-500 ease-in-out text-gray-500 hover:bg-gray-300 focus:outline-none">
               <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" class="h-6 w-6 text-gray-600">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 11a7 7 0 01-7 7m0 0a7 7 0 01-7-7m7 7v4m0 0H8m4 0h4m-4-8a3 3 0 01-3-3V5a3 3 0 116 0v6a3 3 0 01-3 3z"></path>
               </svg>
            </button>
         </span>
         <input type="text" v-model="message" placeholder="Write your message!" @click="clickMes" @keyup.enter="sendMessage" class="w-full focus:outline-none focus:placeholder-gray-400 text-gray-600 placeholder-gray-600 pl-12 bg-gray-200 rounded-md py-3">
         <div class="absolute right-0 items-center inset-y-0 hidden sm:flex ">
            <button type="button" class="inline-flex items-center justify-center rounded-full h-10 w-10 transition duration-500 ease-in-out text-gray-500 hover:bg-gray-300 focus:outline-none">
               <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" class="h-6 w-6 text-gray-600">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15.172 7l-6.586 6.586a2 2 0 102.828 2.828l6.414-6.586a4 4 0 00-5.656-5.656l-6.415 6.585a6 6 0 108.486 8.486L20.5 13"></path>
               </svg>
            </button>
            <button type="button" class="inline-flex items-center justify-center rounded-full h-10 w-10 transition duration-500 ease-in-out text-gray-500 hover:bg-gray-300 focus:outline-none">
               <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" class="h-6 w-6 text-gray-600">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 9a2 2 0 012-2h.93a2 2 0 001.664-.89l.812-1.22A2 2 0 0110.07 4h3.86a2 2 0 011.664.89l.812 1.22A2 2 0 0018.07 7H19a2 2 0 012 2v9a2 2 0 01-2 2H5a2 2 0 01-2-2V9z"></path>
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 13a3 3 0 11-6 0 3 3 0 016 0z"></path>
               </svg>
            </button>
            <button type="button" class="inline-flex items-center justify-center rounded-full h-10 w-10 transition duration-500 ease-in-out text-gray-500 hover:bg-gray-300 focus:outline-none">
               <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" class="h-6 w-6 text-gray-600">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14.828 14.828a4 4 0 01-5.656 0M9 10h.01M15 10h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z"></path>
               </svg>
            </button>
            <button type="button" class="inline-flex items-center justify-center rounded-lg px-4 py-3 transition duration-500 ease-in-out text-white bg-blue-500 hover:bg-blue-400 focus:outline-none">
               <span class="font-bold" @click="sendMessage">Send</span>
               <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" class="h-6 w-6 ml-2 transform rotate-90">
                  <path d="M10.894 2.553a1 1 0 00-1.788 0l-7 14a1 1 0 001.169 1.409l5-1.429A1 1 0 009 15.571V11a1 1 0 112 0v4.571a1 1 0 00.725.962l5 1.428a1 1 0 001.17-1.408l-7-14z"></path>
               </svg>
            </button>
         </div>
      </div>
   </div>

  </div>
  
</template>

<script >
// import HelloWorld from './components/HelloWorld.vue'
import * as signalR from "@microsoft/signalr";

export default  {
  data() {
    return {
      user: "",
      message: "",
      messages: [],
      device: [],
      connectionState: "",
      hubConnection: null,
      active : false,
      activemes: false,
      logo : "",
      gif:".gif",
      userActual: "",
    };
  },

  mounted() {
      this.initializeSignalR();
    },

  methods: {
    initializeSignalR() {
        this.hubConnection = new signalR.HubConnectionBuilder()
          .withUrl("https://localhost:7011/dashboardHub")
          .configureLogging(signalR.LogLevel.Information)
          .build();
  
        this.hubConnection.start().then(() => {
          console.log("SignalR connection");
          this.connectionState = this.hubConnection.state;
          this.registerSignalREventHandlers();
          //this.receiveDevice();
          //this.sendaddress();
        }).catch(err => console.error("Signalr Connection failed han:", err));
        
      //   this.hubConnection.onclose(() => {
      //   this.connectionState = hubConnection.connectionState;
      //  });
      this.connectionState = this.hubConnection.state;
      },

      
      
  
      registerSignalREventHandlers() {
        
        this.hubConnection.on("ReceiveMessage", (user, message) => {
          this.messages.push({ user, message });
          if (message == "")
          {
            this.activemes = true;
          }
          
        }); 
      }, 

      receiveDevice() {
        this.hubConnection.on("ReceivedDevices", (devices) => {
          this.device.push(devices);
        });

      },

      sendaddress() {
        this.hubConnection
            .invoke("SendMessage", "Address1", "Hello")
            .then(() => {
              console.log("Message sent");
            })
            .catch((error) => {
              console.error("Error sending message:", error);
            });
      },

      sendMessage() {
        if (this.user && this.message) {
          this.activemes = false;
          this.hubConnection
            .invoke("SendMessage", this.user, this.message)
            .then(() => {
              console.log("Message sent");
              this.message = "";
            })
            .catch((error) => {
              console.error("Error sending message:", error);
            });
        }
      },

      submit() {
        if (this.user) {
          this.active = true;
          this.logo = this.user.substring(0,1);
          this.userActual = this.user;
        }

      }

  },
};

</script>

<style scoped>
div#nuxt-devtools-anchor {
    display: none;
}

.fab {
  background: rgb(0, 104, 200);
    color: rgb(255, 255, 255);
    width: 40px;
    height: 40px;
    border-radius: 50%;
    margin-left: 7px;
    display: flex;
    flex-direction: column-reverse;
    justify-content: space-evenly;
    align-items: center;
}


.noidung {
  margin-top: 10px;
  height: 426px;
  overflow-x: hidden;
  margin-left: 7px;
    margin-right: 7px;

}

.add {
  background: rgb(0, 104, 200);
    width: 50px;
    height: 30px;
    border-radius: 50%;
    margin-left: 4px;
}
input.inp {
    border-radius: 22px;
    border: 1px solid gray;
    border-color: gray;
    height: 30px;
    width: 402px;
    margin-left: 8px
}
.send {
    background: rgba(251, 251, 251, 0);
    width: 40px;
    height: 40px;
    border-radius: 50%;
    text-align: center;
}
.inname {
  border-radius: 22px;
    border: 1px solid gray;
    border-color: gray;
    height: 30px;
    width: 90%;
    text-align: center;
    font-size: 16px;
    font-weight: 400;
    color: black;
}
.ishiden {
  display : none !important ;
}


.mess {
  display: flex;
  margin-bottom: 3px; 
  align-items: center;
  flex-direction: row;
}
</style>
