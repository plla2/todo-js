# 바닐라 자바스크립트를 활용한 Todo 앱

## 💻 Repo 소개
바닐라 자바스크립트를 활용하여 다크모드 토글버튼과 리스트 추가,삭제,체크를 할 수 있는 사이트입니다.

## 🖋️ 주요 기능 </br>
```
function darkMode() {
  body.setAttribute(
    "data-theme",
    body.getAttribute("data-theme") === "dark" ? "light" : "dark"
  );
  themeIcon.setAttribute(
    "src",
    themeIcon.getAttribute("src") === "images/icon-sun.svg"
      ? "images/icon-moon.svg"
      : "images/icon-sun.svg"
  );
  localStorage.setItem("theme", body.getAttribute("data-theme"));
}
toggleSwitch.addEventListener("click", setTheme);
```
위의 코딩을 통해 밤,낮에 사용하기 편리하도록 토글버튼을 이용하여 다크모드를 구현했다.</br></br>
```
function createToDo(e) {
  let toDoVal = e.target.value;
  if (toDoVal == null || toDoVal == "") {
    alert("Please enter a task");
  } else {
    const toDo = document.createElement("li");
    toDo.classList.add("task");
    toDo.innerHTML += `
    <button class="checkBtn">          
        <img 
        id="checkIcon" 
        src="images/icon-check.svg" 
        alt="check-icon"/>
    </button>
    <span class="toDoText break-word">${toDoVal}</span>
    <img alt="remove" class="remove" src="images/icon-cross.svg">
    `;
 ```
 위의 코딩을 통해 할일을 리스트에 추가하기 위해 toDoval의 입력값이 비었으면 alert, 아니면 toDo의 클래스로 task를 추가하여  innerHTML로 마크업을 추가하도록 구현하였다.</br></br>
 ```
 const bindRemove = (btn) => {
  btn.addEventListener("click", () => {
    const mainPar = btn.parentElement;
    mainPar.remove();
    tasks.pop(mainPar);
    completedTasks.pop(mainPar);
    updateTaskCount();
  });
};
```
위의 코딩을 통해 리스트에서 지우고싶다면 pop()함수로 tasks배열에서 제거하는 식으로 구현을 하였고, 완료된 할일은 completedTasks 배열에서 pop()을 통해 제거를 할 수 있게 구현하였다.</br></br>
```
const bindDone = (btn) => {
  const checkIcon = btn.querySelector("#checkIcon");
  btn.addEventListener("click", () => {
    const mainPar = btn.parentElement;
    btn.classList.toggle("checked");
    checkIcon.style.display = "block";
    mainPar.classList.toggle("completed");
    mainPar.classList.contains("completed")
      ? completedTasks.push(mainPar)
      : completedTasks.pop(mainPar);
    updateTaskCount();
  });
};
```
위의 코딩을 통해 완료된 할일을 체크할 수 있는 버튼을 만들어 completed라는 클래스를 만들어 완료된 할일을 배열에 추가할 수 있게 구현하였다.

## 🖥️ 실행화면
첫 초기화면</br></br>
<img width="794" alt="스크린샷 2023-02-04 오후 5 23 46" src="https://user-images.githubusercontent.com/120915990/216757971-00122dc4-cf88-493e-92d0-61f950649a76.png"></br></br>
다크모드 토글버튼 활성화</br></br>
<img width="795" alt="스크린샷 2023-02-04 오후 5 23 57" src="https://user-images.githubusercontent.com/120915990/216758045-ab06b0c9-0edd-49af-b737-b147061d2fd8.png"></br></br>
할일 추가, 완료표시화면</br></br>
<img width="794" alt="스크린샷 2023-02-04 오후 5 24 34" src="https://user-images.githubusercontent.com/120915990/216758085-c99daa65-cde3-4f1a-9209-d34c84cc0f60.png">


