# pr_Q3
from flask import Flask,request,jsonify
app=Flask(_name_)
students=[]
@app.route('/')
def home():
    return "Monolithic student app running"

@app.route('/add',methods=['POST'])
def add_student():
    data=request.form
    student={"name":data.get("name")}
    students.append(student)
    return {"message":"Student added successfully"}

@app.route('/view',methods=['GET'])
def get_student():
    return jsonify(students)

@app.route('/delete/<int:i>',methods=['DELETE'])
def delete_student(i):
    if i<len(students):
        students.pop(i)
    return jsonify({"message":"Deleted"}) 

if _name_ == '_main_':
    app.run(debug=True)



curl -X POST http://127.0.0.1:5000/add -d "name=agnes"
curl -X GET http://127.0.0.1:5000/view
curl -X DELETE http://127.0.0.1:5000/delete/0
