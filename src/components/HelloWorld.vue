<template>
  <v-container>
    <v-row class="text-center">
        <h1> {{ promise() }} </h1>
        <h1> {{ callback() }} </h1>
        <h1> {{ callbacks() }} </h1>
        <h1> {{ simpleCallBacks() }} </h1>
        <h1> {{ promisesSample() }} </h1>
        <h1> {{ samplePro() }} </h1>
        <h1>hi {{ first(2,function(firstResult,err){
                 if(!err){
                   second(firstResult,function(secondResult,err){
                   if(!err){
                       third(secondResult,function(thirdResult,err){
                         console.log('The result is ',thirdResult)
                       })
                   } })
                } }) }} </h1>
    </v-row>
  </v-container>
</template>

<script>
  export default {
    name: 'HelloWorld',

    data: () => ({
      
    }),
    methods:{
//Promises examples
      promise(){
        const p1 = new Promise((resolve,reject)=>{
                    let isMarried=false;
                    if(isMarried){
                      resolve("Married")
                    } else{
                      reject('Unmarried')
                    }
      }) 

      p1.then((res)=>{
        console.log("He is ",res)
      }).catch((error)=>{
         console.log("He is ",error);
      })
      },
// Callback Functions Examples
      callback(){
        let x=(z,cbf)=>{
            console.log('X is called');
            cbf()
        }

        let y=()=>{
            console.log('Y is called');
        }

        x("Hello",y);
        
      },

      callbacks(){
        const userLeft = false
        const userWatchingCatMeme = false
        let watchTutorialCallBack = (callback,errorCallback) => {
                if(userLeft) {
                  errorCallback({
                    name:'User Left',
                    message: ':('
                  })
                }  else if(userWatchingCatMeme){
                  errorCallback({
                    name: 'USer Watching Cat Meme',
                    message: 'WebDevSimplified < Cat'
                  })
                } else {
                  callback('Thumbs up and you were Succedd')
                }
        }

        watchTutorialCallBack((message) => {
             console.log('success: ' + message);
        },(error) => {
          console.log(error.name + ' ' + error.message);
        })
      },

    // CallBack functions  
    first(value,callback){
          callback(value+2)
    },

    second(value,callback){
          callback(value+2)
    },

    third(value,callback){
          callback(value+2)
    },


    // Simple CallBack Example
    
    simpleCallBacks(){
        let employees=['Akhil','chaitanya','Sathish','Naveen']

        let addNewEmp=(newUser,callback)=>{
          employees.push(newUser)
          console.log('Employee Added');
          callback()
        }

        let allEmployees=()=>{
          console.log("Employees are",employees);
        }

        addNewEmp('Alladi',allEmployees);
     
    },

    //Promises Simple Example
    promisesSample(){
      let number1=5;
      let number2=5;

      let promise1=new Promise((resolve,reject)=>{
          if(number1===number2){
            resolve()
          } else{
            reject()
          }
      })

      promise1.then(()=>{
        console.log('It is Equal')
      }).catch(()=>{
        console.log('Not equal');
      })

    },

    samplePro(){
      // let employees1=['Akhil','chaitanya','Sathish','Naveen']
      return new Promise((resolve,reject)=>{
      let employees=['Akhil','chaitanya','Sathish','Naveen']
      let empl=employees.push('xyz')
         resolve(empl);
         reject()
      })
      .then((emp)=>{
        console.log('Addeded',emp);
      }).catch((error)=>{
        console.log('Not added',error);
      })
    }

    },
  }
</script>
