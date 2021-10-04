로컬 vue 프로젝트 생성
vue create project 
vue add vuetify

로컬호스트 실행
npm run serve

dist 파일 생성
npm run build

나머지는 인터넷^^


부모 -> 자식 parameter 전달

app.vue
```
  <first-region
    v-if="showCalendar"
    :data="item"
    :para="parameter"
    @parse="getEvents"
  ></first-region>
  
  <your-component
    v-else
  ></your-component>
  
  <v-btn @click="show">캘린더</v-btn>

  data: () => ({
    item = ['parents', child'], 
    parameter = ['key': "value" ], 
    showCalendar = false, 
    events: [],
  }),
  methods: {
    show() {
      this.showCalendar = true;
    },
  
```  
FirstRegion.vue
```
    export default {
    name: 'eastlight',
    props: ['data', 'para'],
    
    data: () => ({
      value: '',
      item: ['month', 'week', '4day'],
      events: [],
      type: 'week',
      color: ['black', 'white', 'primary', 'grey']
    }),
    
    
    create: { 
      console.log(this.data);
    }, 
    
    computed: {
      getType() {
        
        ...
    
 ```
 v-if 
  if 조건에 따라 실행
  조건에 맞지 않으면 해당 컴포넌트 생성 x 
  아래 create도 생성하지 않기 때문에 실행되지 않음
  
 v-else
  if조건에 해당하지 않을 때 실행
  
 props
  부모에게 받은 parameter소품 부모의 :변수명 과 props ['변수명'] 이 같아야함
    
 create
  컴포넌트가 생성될 때 최초 1번 실행 
  아마 예상 하건데 위처럼 하면 console에 ['parents', child'] 찍힐 듯
  
  
    
