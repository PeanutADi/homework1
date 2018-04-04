## Part 1 简答题 ##
**1.解释游戏对象（GameObjects）和资源（Assets）的区别与联系。**

区别：游戏对象直接出现在场景中，，一般有玩家，敌人，环境和音乐等虚拟父类。这些父类本身没有实体，但他们的子类包含了游戏中会出现的对象。资源文件夹通常有对象、材质、场景、声音、预设、贴图、脚本、动作，在这些文件夹下可以继续划分。

联系：对象是资源整合的具体表现；资源可以被一个或多个对象使用，有些资源作为模板，可实例化成游戏中具体的对象。

**2.下载几个游戏案例，分别总结资源、对象组织的结构（指资源的目录组织结构与游戏对象树的层次结构）**

资源（Asset）下的结构：
![资源结构](https://img-blog.csdn.net/20180326222359393?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1BlYW51dERvMXQ=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

如截图所示，字体，图片，脚本，场景的均在Asset目录下。

**3.编写一个代码，使用 debug 语句来验证 MonoBehaviour 基本行为或事件触发的条件**

代码：

```

using System.Collections;

using System.Collections.Generic;

using UnityEngine;

public class test : MonoBehaviour {

	// Use this for initialization

	void Start () {

		Debug.Log ("Starting...");

	}

	// Update is called once per frame

	void Update () {

		Debug.Log ("Updating...");

	}

	void Awake(){

		Debug.Log("Awaking...");

	}

	void FixedUpdate(){

		Debug.Log ("FixedUpdating...");

	}

	void LateUpdate(){

		Debug.Log ("LateUpdating...");

	}

	void OnGUI() {

		Debug.Log ("In OnGUI");

	}

	void OnDisable() {

		Debug.Log ("In OnDisable");

	}

	void OnEnable() {

		Debug.Log ("In OnEnable");

	}

}
```


运行结果：
![结果截图1](https://img-blog.csdn.net/20180326222656282?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1BlYW51dERvMXQ=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

![结果截图2](https://img-blog.csdn.net/20180326222743580?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1BlYW51dERvMXQ=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)
**4.查找脚本手册，了解 GameObject，Transform，Component 对象**

**Description：**

GameObject 游戏物体：继承自Object类，是Unity场景里所有实体的基类

Transform 变换：继承自Component，IEnumberable类，包括一个物体的位置、旋转和缩放。场景中的每一个物体都有一个Transform属性。用于储存并操控物体的位置、旋转和缩放。每一个Transform可以有一个父级，允许你分层次应用位置、旋转和缩放。可以在Hierarchy面板查看层次关系。他们也支持使用计数器，因此你可以使用循环遍历子物体。

Component 组件：继承自Object类，是一切和游戏物体有关类的基类。
![题目图片](https://img-blog.csdn.net/20180326222935721?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1BlYW51dERvMXQ=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

**描述table对象的属性：**

Table是GameObject类的一个实例，第一个选择框是 activeSelf 属性。

Tag属性是游戏物体的标签，可用于查找游戏物体且效率较高，对应tag变量,第一个选择框对应CompareTag()方法。Layer属性是指游戏物体所在的层，Unity中默认已有8种Layer，一个层的范围是在[0...32]之间，对应layer变量。

**table对象的Transform属性：**

是Transform类的一个实例。

postion:在世界空间坐标中的相对位置，对应position变量，后面的xyz对应TransformPoint()方法。

rotation:物体变换的旋转角度，作为Quaternion储存，对应rotation变量，xyz对应Rotate（）方法的三个参数。

scale:相对于父级物体的缩放，对应localScale变量。

**table的部件：**

Mesh Filter:网格过滤器，作为物体与Mesh的接口，输入窗口的作用是接入实例化的Mesh

Mesh
Renderer：网格渲染器，渲染网格。第一个窗口对应castShadows()方法，勾选框对应receiveShadows（）方法，之后的窗口对应motionVectors()方法。Light
Probes是LightProbes的对象。Anchor Override找不到具体对应的api。

Box
Collider:盒碰撞器。第一个勾选框对应isTrigger变量，之后的选择框对应material变量，之后分别对应BoxCollider.center和BoxCollider.size

**UML图：**
![UML图](https://img-blog.csdn.net/20180326223008165?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1BlYW51dERvMXQ=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)
**5. 整理相关学习资料，编写简单代码验证以下技术的实现：**

**查找对象**

通过调用GameObject.Find(string name)方法实现：

代码：

```
using UnityEngine;

using System.Collections;

public class Example : MonoBehaviour {

	public GameObject hand;

	void forExample() {

		hand = GameObject.Find("Hand");

	}

}

```


**添加子对象**

通过调用GameObject.CreatePrimitive(PrimitiveType \_ttype)方法实现

代码：

```
using UnityEngine;

using System.Collections;

public class ExampleClass : MonoBehaviour {

	void Start() {

		GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);

	}

}
```


**遍历对象树**

代码：

```

void Traversal(GameObject obj){

	int i = 0;

	while(i \< obj.transform.chilCount){

		Transform p=obj.transform.GetChild(i);

		//对p进行遍历要进行的动作

		if(p.childCount \> 0) Traversal(p);

		i++;

	}

}
```


**清除所有子对象**

代码：

```
void DESTraversal(GameObject obj){

	int i = 0;

	while(i \< obj.transform.chilCount){

		Transform p=obj.transform.GetChild(i);

		if(p.childCount \> 0) Traversal(p);

		Destroy(p.gameObject);

		i++;
	
	}

}

```

**6.资源预设（Prefabs）与 对象克隆 (clone)**

**名词解释：**

Prefabs（预设）是一种资源类型，可被重复使用的游戏对象。它可以被置入多个场景中，又或者能够在一个场景中被多次置入。

Clone（克隆）即创建一个该物体属性相同又不相关的新实例。

**预设的好处：**

预设可以看做游戏资源的模板。当在游戏场景中创建一个预设时即创建了一个他的实例。预设是相互关联的，当对预设进行更改时，这些更改将会作用于与之相连的所有实例。

**预设与克隆的关系：**

二者行为相似，但克隆对象不会随着被克隆对象的改变而改变。

**将table实例化：**

```

public class NewBehaviourScript : MonoBehaviour {

	private string prePath = "prefabs/table";

	private GameObject MyTable;

	void Start () {

		MyTable = (GameObject)Instantiate(Resource.Load(prePath), new Vector(4, 0, 0),Quaternion.identity) ;

	}

}
```


**7. 尝试解释组合模式（Composite Pattern / 一种设计模式）。使用BroadcastMessage() 方法向子对象发送消息**

组合模式通过树形结构来表现部分与整体的层次。因为要求简单对象与复杂对象都要有同样的接口，所以能对对象进行一致处理。

**父类对象方法：**

```
void Start () {

	this.BroadcastMessage("HelloSon");

}
```



**子类对象方法：**

```

Void HelloSon() {

	Debug.Log("CallReceived");

}
```
## Part2 编程实践：井字棋 ##

见我的下一篇博客
[井字棋实现](https://blog.csdn.net/peanutdo1t/article/details/79706261)

**项目地址**

[TicTacToe](https://github.com/PeanutADi/LearningUnityCoding)

**完成效果图**

![效果图](https://img-blog.csdn.net/20180326232256972?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1BlYW51dERvMXQ=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

使用AI有些不恰当的是AI是无智能的随机下棋。

Turns下面的蓝点表示该哪名玩家 下棋，Reset重置，Result显示结果Ai 按钮代表下一步棋AI会随机下一步，如果已经分出胜负的话这个按钮就没用了。

私有成员变量：

```
	private int turn = 1;    //1 - Player 1, 0 - Player 2 
	private int[,] board = new int[3,3];   //棋盘
	private int result = 0;  //0代表未结束，1为1赢，2为2赢，3为平局

	//背景及棋子
	public Texture2D img;  
	public Texture2D img1;  
	public Texture2D img2; 
```

初始化方法：Reset()

```
// Use this for initialization 
	void Reset() { 
		result = 0;
		turn = 1;    
		for (int i=0; i<3; ++i) {    
			for (int j=0; j<3; ++j) {    
				board[i,j] = 0;    
			}    
		}  
	}  
```

Start()方法也通过调用Reset()方法实现初始化

显示棋盘和下棋的逻辑实现：

因为OnGui是每帧刷新所以我们只需要考虑每个瞬时的动作，即构建按钮后这个按钮是否被按下，若被按下则记录。

```
for (int i=0; i<3; ++i) {    
			for (int j=0; j<3; ++j) {    
				if (board [i, j] == 1)    
					GUI.Button (new Rect (210 + i * 50, 140 + j * 50, 50, 50), img1);  
				if (board [i, j] == 2)  
					GUI.Button (new Rect (210 + i * 50, 140 + j * 50, 50, 50), img2);  
				if (GUI.Button (new Rect (210 + i * 50, 140 + j * 50, 50, 50), "")) {    
					if (result == 0) {    
						if (turn == 1)    
							board [i, j] = 1;  
						else    
							board [i, j] = 2;    
						turn = 1-turn;    
					}    
				}    
			}  
		}
```
实现随机下一步：

只有当按钮被点到而且游戏仍在进行中才会执行操作。获取两个随机数并保证不与已有的棋子重叠，重叠则换位置，之后通过修改board来表示已经下棋。

```
		//A random step
		if (GUI.Button (new Rect (50, 220, 100, 50), "Ai plays 1 step") && result == 0) {
			int ri = (int)Random.Range (0, 20);
			ri %= 3;
			int rj = (int)Random.Range (0, 20);
			rj %= 3;
			int cnt = 0;
			while (board [ri, rj] != 0) {
				ri = ri + 1;
				ri %= 3;
				cnt++;
				if (cnt == 3)
					break;
			}
			cnt = 0;
			while (board [ri, rj] != 0) {
				rj = rj + 1;
				rj %= 3;
				if (cnt == 3)
					break;
			}
			int flag = 0;
			if (board [ri, rj] == 0)
				flag = 1;
			if (turn == 1 && flag == 1)    
				board [ri, rj] = 1;  
			else if(turn == 0 && flag == 1)   
				board [ri, rj] = 2;    
			turn = 1-turn;    
		}
```

检查结果：

1.若有一方形成三子连线则这方获胜

2.若无三子连线且下满九子则平局

```
	//Check the result
	int check() {    
		int count = 0;
		for (int i = 0; i < 3; i++) {
			for (int j = 0; j < 3; j++) {
				if (board [i, j] != 0)
					count++;
			}
		}
		for (int i=0; i<3; ++i) {    
			if (board[i,0]!=0 && board[i,0]==board[i,1] && board[i,1]==board[i,2]) {    
				return board[i,0];    
			}    
		}    
		for (int j=0; j<3; ++j) {    
			if (board[0,j]!=0 && board[0,j]==board[1,j] && board[1,j]==board[2,j]) {    
				return board[0,j];    
			}    
		}    
		if (board[1,1]!=0 &&    
			board[0,0]==board[1,1] && board[1,1]==board[2,2] ||    
			board[0,2]==board[1,1] && board[1,1]==board[2,0]) {    
			return board[1,1];    
		}    
		if (count == 9)
			return 3;
		return 0;    
	}    
```

**完整代码**

```
using UnityEngine;  
using System.Collections;  

public class TicTacToe : MonoBehaviour {  

	private int turn = 1;    //1 - Player 1, 0 - Player 2 
	private int[,] board = new int[3,3];   
	private int result = 0;  //0代表未完成，1 - 1 wins，2-2 wins，3-平局

	//背景及棋子
	public Texture2D img;  
	public Texture2D img1;  
	public Texture2D img2;  

	// Use this for initialization 
	void Reset() { 
		result = 0;
		turn = 1;    
		for (int i=0; i<3; ++i) {    
			for (int j=0; j<3; ++j) {    
				board[i,j] = 0;    
			}    
		}  
	}  
 
	void Start () {  
		Reset ();  
	}  

	void OnGUI() {   

		//Welcome's fontstyle
		GUIStyle fontStyle = new GUIStyle();  
		fontStyle.normal.background = null;   
		fontStyle.normal.textColor= new Color(1, 0, 0);    
		fontStyle.fontSize = 20;   

		//Result's fontstyle
		GUIStyle fontStyle2 = new GUIStyle();  
		fontStyle2.normal.background = null;   
		fontStyle2.normal.textColor= new Color(1, 0, 1);    
		fontStyle2.fontSize = 15;   

		//Players & turns' fontstyle
		GUIStyle fontStyle3 = new GUIStyle();  
		fontStyle3.normal.background = null;   
		fontStyle3.normal.textColor= new Color(0, 0, 1);    
		fontStyle3.fontSize = 15;   

		//dots' fontstyle
		GUIStyle fontStyle4 = new GUIStyle();  
		fontStyle4.normal.background = null;   
		fontStyle4.normal.textColor= new Color(0, 0, 1);    
		fontStyle4.fontSize = 40;   

		//Background
		GUI.Label (new Rect (0, 0, 640,360), img);  

		//Welcome slogan
		GUI.Label (new Rect (190, 15, 100, 100), "Welcome to TicTacToe",fontStyle);  

		//Show the Players
		GUI.Label (new Rect (50, 50, 50, 50), img1);  
		GUI.Label (new Rect (120, 75, 100, 50), "Player1",fontStyle3); 
		GUI.Label (new Rect (50, 120, 50, 50), img2);  
		GUI.Label (new Rect (120, 145, 100, 50), "Player2",fontStyle3);

		//Show the turns
		GUI.Label (new Rect (30, 25, 100, 50), "Turns:", fontStyle3);
		if (turn == 1) {
			GUI.Label (new Rect (30, 50, 100, 50), "·", fontStyle4);
		} else {
			GUI.Label (new Rect (30, 120, 100, 50), "·", fontStyle4);
		}

		//Reset button
		if (GUI.Button (new Rect (250, 60, 70, 50), "RESET"))  
			Reset ();  

		// Show the board
		for (int i=0; i<3; ++i) {    
			for (int j=0; j<3; ++j) {    
				if (board [i, j] == 1)    
					GUI.Button (new Rect (210 + i * 50, 140 + j * 50, 50, 50), img1);  
				if (board [i, j] == 2)  
					GUI.Button (new Rect (210 + i * 50, 140 + j * 50, 50, 50), img2);  
				if (GUI.Button (new Rect (210 + i * 50, 140 + j * 50, 50, 50), "")) {    
					if (result == 0) {    
						if (turn == 1)    
							board [i, j] = 1;  
						else    
							board [i, j] = 2;    
						turn = 1-turn;    
					}    
				}    
			}  
		}

		//Show the result
		GUI.Label (new Rect (50, 185, 100, 50), "Result:",fontStyle2);
		result = check ();    
		if (result == 1) {    
			GUI.Label (new Rect (105, 185, 100, 50), "Player1 wins!", fontStyle2);    
		} else if (result == 2) {    
			GUI.Label (new Rect (105, 185, 100, 50), "Player2 wins!", fontStyle2);    
		} else if (result == 3) {
			GUI.Label (new Rect (105, 185, 100, 50), "No one wins", fontStyle2); 
		} else {
			GUI.Label (new Rect (105, 185, 100, 50), "Playing...", fontStyle2);
		} 

		//A random step
		if (GUI.Button (new Rect (50, 220, 100, 50), "Ai plays 1 step") && result == 0) {
			int ri = (int)Random.Range (0, 20);
			ri %= 3;
			int rj = (int)Random.Range (0, 20);
			rj %= 3;
			int cnt = 0;
			while (board [ri, rj] != 0) {
				ri = ri + 1;
				ri %= 3;
				cnt++;
				if (cnt == 3)
					break;
			}
			cnt = 0;
			while (board [ri, rj] != 0) {
				rj = rj + 1;
				rj %= 3;
				if (cnt == 3)
					break;
			}
			int flag = 0;
			if (board [ri, rj] == 0)
				flag = 1;
			if (turn == 1 && flag == 1)    
				board [ri, rj] = 1;  
			else if(turn == 0 && flag == 1)   
				board [ri, rj] = 2;    
			turn = 1-turn;    
		}
	}  
 
	//Check the result
	int check() {    
		int count = 0;
		for (int i = 0; i < 3; i++) {
			for (int j = 0; j < 3; j++) {
				if (board [i, j] != 0)
					count++;
			}
		}
		for (int i=0; i<3; ++i) {    
			if (board[i,0]!=0 && board[i,0]==board[i,1] && board[i,1]==board[i,2]) {    
				return board[i,0];    
			}    
		}    
		for (int j=0; j<3; ++j) {    
			if (board[0,j]!=0 && board[0,j]==board[1,j] && board[1,j]==board[2,j]) {    
				return board[0,j];    
			}    
		}    
		if (board[1,1]!=0 &&    
			board[0,0]==board[1,1] && board[1,1]==board[2,2] ||    
			board[0,2]==board[1,1] && board[1,1]==board[2,0]) {    
			return board[1,1];    
		}    
		if (count == 9)
			return 3;
		return 0;    
	}    
}  
```
