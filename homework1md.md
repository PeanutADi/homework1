## Part 1 ����� ##
**1.������Ϸ����GameObjects������Դ��Assets������������ϵ��**

������Ϸ����ֱ�ӳ����ڳ����У���һ������ң����ˣ����������ֵ����⸸�ࡣ��Щ���౾��û��ʵ�壬�����ǵ������������Ϸ�л���ֵĶ�����Դ�ļ���ͨ���ж��󡢲��ʡ�������������Ԥ�衢��ͼ���ű�������������Щ�ļ����¿��Լ������֡�

��ϵ����������Դ���ϵľ�����֣���Դ���Ա�һ����������ʹ�ã���Щ��Դ��Ϊģ�壬��ʵ��������Ϸ�о���Ķ���

**2.���ؼ�����Ϸ�������ֱ��ܽ���Դ��������֯�Ľṹ��ָ��Դ��Ŀ¼��֯�ṹ����Ϸ�������Ĳ�νṹ��**

��Դ��Asset���µĽṹ��
![��Դ�ṹ](https://img-blog.csdn.net/20180326222359393?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1BlYW51dERvMXQ=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

���ͼ��ʾ�����壬ͼƬ���ű��������ľ���AssetĿ¼�¡�

**3.��дһ�����룬ʹ�� debug �������֤ MonoBehaviour ������Ϊ���¼�����������**

���룺

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


���н����
![�����ͼ1](https://img-blog.csdn.net/20180326222656282?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1BlYW51dERvMXQ=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

![�����ͼ2](https://img-blog.csdn.net/20180326222743580?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1BlYW51dERvMXQ=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)
**4.���ҽű��ֲᣬ�˽� GameObject��Transform��Component ����**

**Description��**

GameObject ��Ϸ���壺�̳���Object�࣬��Unity����������ʵ��Ļ���

Transform �任���̳���Component��IEnumberable�࣬����һ�������λ�á���ת�����š������е�ÿһ�����嶼��һ��Transform���ԡ����ڴ��沢�ٿ������λ�á���ת�����š�ÿһ��Transform������һ��������������ֲ��Ӧ��λ�á���ת�����š�������Hierarchy���鿴��ι�ϵ������Ҳ֧��ʹ�ü���������������ʹ��ѭ�����������塣

Component ������̳���Object�࣬��һ�к���Ϸ�����й���Ļ��ࡣ
![��ĿͼƬ](https://img-blog.csdn.net/20180326222935721?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1BlYW51dERvMXQ=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

**����table��������ԣ�**

Table��GameObject���һ��ʵ������һ��ѡ����� activeSelf ���ԡ�

Tag��������Ϸ����ı�ǩ�������ڲ�����Ϸ������Ч�ʽϸߣ���Ӧtag����,��һ��ѡ����ӦCompareTag()������Layer������ָ��Ϸ�������ڵĲ㣬Unity��Ĭ������8��Layer��һ����ķ�Χ����[0...32]֮�䣬��Ӧlayer������

**table�����Transform���ԣ�**

��Transform���һ��ʵ����

postion:������ռ������е����λ�ã���Ӧposition�����������xyz��ӦTransformPoint()������

rotation:����任����ת�Ƕȣ���ΪQuaternion���棬��Ӧrotation������xyz��ӦRotate��������������������

scale:����ڸ�����������ţ���ӦlocalScale������

**table�Ĳ�����**

Mesh Filter:�������������Ϊ������Mesh�Ľӿڣ����봰�ڵ������ǽ���ʵ������Mesh

Mesh
Renderer��������Ⱦ������Ⱦ���񡣵�һ�����ڶ�ӦcastShadows()��������ѡ���ӦreceiveShadows����������֮��Ĵ��ڶ�ӦmotionVectors()������Light
Probes��LightProbes�Ķ���Anchor Override�Ҳ��������Ӧ��api��

Box
Collider:����ײ������һ����ѡ���ӦisTrigger������֮���ѡ����Ӧmaterial������֮��ֱ��ӦBoxCollider.center��BoxCollider.size

**UMLͼ��**
![UMLͼ](https://img-blog.csdn.net/20180326223008165?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1BlYW51dERvMXQ=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)
**5. �������ѧϰ���ϣ���д�򵥴�����֤���¼�����ʵ�֣�**

**���Ҷ���**

ͨ������GameObject.Find(string name)����ʵ�֣�

���룺

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


**����Ӷ���**

ͨ������GameObject.CreatePrimitive(PrimitiveType \_ttype)����ʵ��

���룺

```
using UnityEngine;

using System.Collections;

public class ExampleClass : MonoBehaviour {

	void Start() {

		GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);

	}

}
```


**����������**

���룺

```

void Traversal(GameObject obj){

	int i = 0;

	while(i \< obj.transform.chilCount){

		Transform p=obj.transform.GetChild(i);

		//��p���б���Ҫ���еĶ���

		if(p.childCount \> 0) Traversal(p);

		i++;

	}

}
```


**��������Ӷ���**

���룺

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

**6.��ԴԤ�裨Prefabs���� �����¡ (clone)**

**���ʽ��ͣ�**

Prefabs��Ԥ�裩��һ����Դ���ͣ��ɱ��ظ�ʹ�õ���Ϸ���������Ա������������У��ֻ����ܹ���һ�������б�������롣

Clone����¡��������һ��������������ͬ�ֲ���ص���ʵ����

**Ԥ��ĺô���**

Ԥ����Կ�����Ϸ��Դ��ģ�塣������Ϸ�����д���һ��Ԥ��ʱ��������һ������ʵ����Ԥ�����໥�����ģ�����Ԥ����и���ʱ����Щ���Ľ�����������֮����������ʵ����

**Ԥ�����¡�Ĺ�ϵ��**

������Ϊ���ƣ�����¡���󲻻����ű���¡����ĸı���ı䡣

**��tableʵ������**

```

public class NewBehaviourScript : MonoBehaviour {

	private string prePath = "prefabs/table";

	private GameObject MyTable;

	void Start () {

		MyTable = (GameObject)Instantiate(Resource.Load(prePath), new Vector(4, 0, 0),Quaternion.identity) ;

	}

}
```


**7. ���Խ������ģʽ��Composite Pattern / һ�����ģʽ����ʹ��BroadcastMessage() �������Ӷ�������Ϣ**

���ģʽͨ�����νṹ�����ֲ���������Ĳ�Ρ���ΪҪ��򵥶����븴�Ӷ���Ҫ��ͬ���Ľӿڣ������ܶԶ������һ�´���

**������󷽷���**

```
void Start () {

	this.BroadcastMessage("HelloSon");

}
```



**������󷽷���**

```

Void HelloSon() {

	Debug.Log("CallReceived");

}
```
## Part2 ���ʵ���������� ##

���ҵ���һƪ����
[������ʵ��](https://blog.csdn.net/PeanutDo1t/article/details/79706261%20TicTacToe%E5%AE%9E%E6%88%98)