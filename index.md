<!DOCTYPE html>
<html>
<body>
<h1>Hello World</h1>
<p>I'm hosted with GitHub Pages.</p>
</body>
<script>
import React, {Component} from "react";
import "./style.css";
class Categories extends Component{
  constructor(){
    super();
    this.state={
      data:false
     // jokes:[],
     // errorMsg:''
    }
  }
  ComponentDidMount(){
    /*axios.get('https://api.chucknorris.io/jokes/categories')
      .then(response => {
        console.log(response)
        this.setState({jokes: response.data})
      })
      .catch(error => {
        console.log(error)
        this.setState({errorMsg:'Error retrieving data'})
      })*/
      let url = "https://api.chucknorris.io/jokes/categories";
      fetch(url,{
        method:'GET',
        headers:{
          'Accept':'application/json',
          'Content-Type':'application/json',
        }
      }).then((result)=>{
        result.json().then((resp)=>{
          
          this.setState({data:resp})
        })
      })
  }
  render(){
    const data=this.state.data;
    console.warn(data);
    return(
      <div>
      List of Categories
      {
        data ?
        <div>
        :<p>Name: {data.value}</p>
        </div>
        :<p>Please Wait..</p>
      }
      
      
      </div>
    )
  }
} 
export default Categories
</script>
</html>