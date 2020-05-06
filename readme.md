 # Documentation of JSON & AJAX AND ANGULAR  
## JSON & AJAX CRUD


## Table of content
-    Definition
-    Create 
-    Update
-    Edit
-    Delete
### Defintion:
JavaScript Object Notation is an open standard file format, and data interchange  format, that  uses human-readable text to store and transmit data objects consisting of attribute–value pairsand array data types.
#code:
  $(document).ready(function () {
		$("#addbtn").click(function (){

		var id = $("#id").val();
		var name = $("#name").val();
		var age = $("#age").val();
		var height = $("#height").val();
		var cnic = $("#cnic").val();


		var jsonObj = { ID: id , Name: name , Age: age , Height: height , CNIC: cnic};
		console.log(jsonObj);

### Create Operation:
First create the website front hand profile and its instruments like table, form, buttons and complete font hand.  
#code:
 <div class="container">
        <h2>
            Add Person<h2>

                <form>

                    <div class="form-group row">
                        <lable class="col-sm-2 col-form-lable">Id</lable>
                        <div class="col-sm-10">
                            <input type="text" class="form-control" id="id" placeholder="Id">
                        </div>
                    </div>

                    <div class="form-group row">
                        <lable class="col-sm-2 col-form-lable">Name</lable>
                        <div class="col-sm-10">
                            <input type="text" class="form-control" id="name" placeholder="Name">
                        </div>
                    </div>

                    <div class="form-group row">
                        <lable class="col-sm-2 col-form-lable">Age</lable>
                        <div class="col-sm-10">
                            <input type="text" class="form-control" id="age" placeholder="Age">
                        </div>
                    </div>

                    <div class="form-group row">
                        <lable class="col-sm-2 col-form-lable">Height</lable>
                        <div class="col-sm-10">
                            <input type="text" class="form-control" id="height" placeholder="Height">
                        </div>
                    </div>

                    <div class="form-group row">
                        <lable class="col-sm-2 col-form-lable">CNIC</lable>
                        <div class="col-sm-10">
                            <input type="text" class="form-control" id="cnic" placeholder="CNIC">
                        </div>
                    </div>

                    <div class="form-group row">
                        <div class="col-sm-2"></div>
                        <div class="col-sm-10">
                            <button type="button" class="btn btn-primary" id="addbtn">Add Person</button>
                        </div>
                    </div>

                </form>






### Update:
When you have to be done fronthand section then you appling CURD operation on the website properly.If you add data in 
your website and you want to update person's data you just open your web page and update as you want. You can see below the 
updating.

#code:
$("#updateButton").click(function (){
		
		var id = $("#eid").val();
		var name = $("#ename").val();
		var age = $("#eage").val();
		var height = $("#eheight").val();
		var cnic = $("#ecnic").val();		
		var jsonObj = { ID: id , Name: name , Age: age , Height: height , CNIC: cnic};
		var Url = "http://labapi.somee.com/api/Person/" + id;



### Edit:
If you want to add data on your website any person you just insert the data on the field. You just see the below how to add / edit the data.
#code:
           $.ajax({
                    type: "GET",
                    url: editUrl,
                    success: function (res) {
                        $("#eid").val(res.ID);
                        $("#ename").val(res.Name);
                        $("#eage").val(res.Age);
                        $("#eheight").val(res.Height);
                        $("#ecnic").val(res.CNIC);
                    },
                    failure: function (res) {
                        alert("Failed");
                    },
                    error: function (res) {
                        alert("Error");
                    }
                });
        }





### Delete:
If someone leave you company and you want to  delete the data of that person just open the profile of person and delete the data.
#code:
            $.ajax({
                    type: "DELETE",
                    url: delUrl,
                    success: function (res) {
                        getPersonData();
                    },
                    failure: function (res) {
                        alert("Failed");
                    },
                    error: function (res) {
                        alert("Error");
                    }
                });
        }





# ANGULAR CRUD
## Table of Content
-    Definition
-    Controller
-    Create
-    Update
-    Edit
-    Delete

### Definition:
AngularJS is a structural framework for dynamic web applications. It lets you use HTML as your template language and lets you 
extend HTML's syntax to express your application components clearly and succinctly. Its data binding and dependency injection 
eliminate much of the code you currently have to write.

#code:
 <table class="table table-hover">
            <thead>
                <tr>
                    <th>ID</th>
                    <th>Name</th>
                    <th>CNIC</th>
                    <th>Age</th>
                    <th>Height</th>
                </tr>
            </thead>
            <tbody ng-repeat="person in personList">
                <tr>
                    <td>{{person.ID}} </td>
                    <td>{{person.Name}}</td>
                    <td>{{person.CNIC}}</td>
                    <td>{{person.Age}}</td>
                    <td>{{person.Height}}</td>
                    <td><button class="btn btn-info" data-toggle="modal" data-target="#exampleModal" ng-click="editPerson(person.ID)">Edit</button></td>
                    <td><button class="btn btn-danger" ng-click="deleteData(person)">Delete </button></td>

                </tr>
            </tbody>
        </table>



### Controller:
A controller is defined using ng-controller directive. A controller is a JavaScript object that contains attributes/properties, and functions. ... The property fullName is the function of $scope.

#code:
var myapp = angular.module("myApp", []);
	myapp.controller('myController', function($scope, $http) {
    URL = "https://fawadlab.herokuapp.com/person/";
    

        $http.get(URL).then(function (result) {

            $scope.personList = result.data;

        });

### Create:
Angular is quit easy to SJON. First create the website front hand profile and its instruments like table, form, buttons and complete font hand.Here you can see my website fronthand complete code.
#code:
<body>
    <div class="container" ng-app="myApp" ng-controller="myController">
       
        <form>
            <h1>Person Data</h1>
            <div class="col-lg-4">

                <div class="form-group">
                    <label for="Name">Name:</label>
                    <input type="text" class="form-control" ng-model="User_Name" placeholder="Name">
                </div>
                <div class="form-group">
                    <label for="CNIC">CNIC:</label>
                    <input type="text" class="form-control" ng-model="User_CNIC" placeholder="CNIC">
                </div>
                <div class="form-group">
                    <label for="Age">Age:</label>
                    <input type="text" class="form-control" ng-model="User_Age" placeholder="Age">
                </div>
                <div class="form-group">
                    <label for="Height">Height:</label>
                    <input type="text" class="form-control" ng-model="User_Height" placeholder="Height">
                </div>

                <button ng-click="addPerson()" type="button" id="btnSubmit" class="btn btn-primary">Submit</button>
            </div>
        </form>


        <table class="table table-hover">
            <thead>
                <tr>
                    <th>ID</th>
                    <th>Name</th>
                    <th>CNIC</th>
                    <th>Age</th>
                    <th>Height</th>
                </tr>
            </thead>
            <tbody ng-repeat="person in personList">
                <tr>
                    <td>{{person.ID}} </td>
                    <td>{{person.Name}}</td>
                    <td>{{person.CNIC}}</td>
                    <td>{{person.Age}}</td>
                    <td>{{person.Height}}</td>
                    <td><button class="btn btn-info" data-toggle="modal" data-target="#exampleModal" ng-click="editPerson(person.ID)">Edit</button></td>
                    <td><button class="btn btn-danger" ng-click="deleteData(person)">Delete </button></td>

                </tr>
            </tbody>
        </table>


        <!-- Modal -->
        <div class="modal fade" id="exampleModal" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
            <div class="modal-dialog" role="document">
                <div class="modal-content">
                    <div class="modal-header">
                        <h5 class="modal-title" id="exampleModalLabel">Modal title</h5>
                        <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                            <span aria-hidden="true">&times;</span>
                        </button>
                    </div>
                    <div class="modal-body">

                        <div class="form-group">
                            <label for="Name">Name:</label>
                            <input type="text" class="form-control" placeholder="Name" ng-model="User_name">
                        </div>
                        <div class="form-group">
                            <label for="CNIC">CNIC:</label>
                            <input type="text" class="form-control" placeholder="CNIC" ng-model="User_cnic">
                        </div>
                        <div class="form-group">
                            <label for="Age">Age:</label>
                            <input type="text" class="form-control" placeholder="Age" ng-model="User_age">
                        </div>
                        <div class="form-group">
                            <label for="Height">Height:</label>
                            <input type="text" class="form-control" placeholder="Height" ng-model="User_height">
                        </div>
                    </div>
                    <div class="modal-footer">
                        <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
                        <button type="button" class="btn btn-primary" ng-click="saveChanges()">Save changes</button>
                    </div>
                </div>
            </div>
        </div>


    </div>

</body>
</html>

### Update:
If you want to update any person data just open its form and update it.

#code:
$scope.saveChanges = function () {
        url =  "https://fawadlab.herokuapp.com/person/" + person.ID;
        var obj = { "Name": $scope.User_name, "CNIC": $scope.User_cnic, "Age": $scope.User_age, "Height": $scope.User_height };
        console.log(obj);

        //$http PUT function
        $http.put(url, obj).then(function successCallback(response) {

            
            Swal.fire(
                'Good job!',
                'Record Updated Successfully!',
                'success'
            )

        }, function errorCallback(response) {

            alert("Error. while updating user Try Again!");

        });

    };



### Edit:
When a person comes to your company and join it then you want to enter that person record open website and insert the data
on it.
#code:
$scope.editPerson = function (id)
    {
        console.log(id);
        editURL = "https://fawadlab.herokuapp.com/person/" + id;
        $http.get(editURL).then(function (result)
        {

            person = result.data;
            
            $scope.User_name = person.Name;
            $scope.User_cnic = person.CNIC;
            $scope.User_age = person.Age;
            $scope.User_height = person.Height;
        })
   
    }




### Delete:
If any enployee want to leave the company and company owner want to delete the record of the enployee just see the below how to
delete record.
#code:
 $scope.deleteData = function (user) {

        //$http DELETE function
        $http({

            method: 'DELETE',
            url: "https://fawadlab.herokuapp.com/person/" + user.ID

        }).then(function successCallback(response) {

            
            Swal.fire(
                'Good job!',
                'Record Deleted Successfully!',
                'success'
            )
            var index = $scope.personList.indexOf(user);
            $scope.personList.splice(index, 1);

        }, function errorCallback(response) {

            alert("Error. while deleting user Try Again!");

        });

    };



