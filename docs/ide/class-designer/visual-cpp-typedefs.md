---
title: "クラス デザイナーにおける Visual C++ の typedef | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.classdesigner.typedef
- vs.classdesigner.aliasofline
helpviewer_keywords: Class Designer [Visual Studio], typedefs
ms.assetid: c1984108-71fc-4d3a-b4d4-3eac2c6b4ebf
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 63bd8657d62a05edb1c9772776ca1216a0eee5ee
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="visual-c-typedefs-in-class-designer"></a>クラス デザイナーにおける Visual C++ の typedef
typedef ステートメントは、名前とその基になる型との間に間接参照のレイヤーを 1 つ以上作成します。 クラス デザイナーでは、キーワード `typedef` などで宣言される C++ の typedef 型をサポートしています。  
  
```cpp
typedef class coord  
{  
   void P(x,y);  
   unsigned x;  
   unsigned y;  
} COORD;  
```  
  
この型を使用して、インスタンスを宣言することができます。  
  
`COORD OriginPoint;`  
  
名前のない typedef を宣言することもできますが、クラス デザイナーでは指定したタグ名が使用されず、クラス ビューで生成される名前が使用されます。 たとえば、次の宣言は有効ですが、クラス ビューとクラス デザイナーでは **__unnamed** という名前のオブジェクトで表示されます。  
  
```cpp
typedef class coord  
{  
   void P(x,y);  
   unsigned x;  
   unsigned y;  
};  
```  
  
`typedef` 型の使用の詳細については、「[typedef 指定子](https://msdn.microsoft.com/en-us/library/05w82thz.aspx)」を参照してください。  
  
C++ の typedef 図形には、typedef で指定された型の図形があります。 たとえば、ソースで `typedef class` が宣言されている場合、図形の角が丸くなり、**Class** のラベルが付きます。 `typedef struct` の場合、図形の角は四角で、**Struct** のラベルが付きます。  
  
クラスと構造体にはその内部で宣言された、入れ子にされた typedef を含めることができるため、クラスと構造体の図形では、入れ子にされた typedef 宣言を入れ子にされた図形として表示することができます。  
  
typedef の図形では、コンテキスト メニューとして **[関連として表示]** および **[コレクションの関連として表示]** のコマンドをサポートしています。  
  
次に、クラス デザイナーでサポートされる typedef 型の例を挙げます。  
  
`typedef type name`  
  
*name* : *type*  
  
Typedef  
  
可能であれば、型 *name* とつながる関連線を描画します。  
  
`typedef void (*func)(int)`  
  
`func: void (*)(int)`  
  
Typedef  
  
関数ポインターの typedef。 関連線は描画されません。  
  
ソースの型が関数ポインターの場合、クラス デザイナーに typedef は表示されません。  
  
```cpp
typedef int MyInt;  
class A {  
   MyInt I;  
};  
```  
  
`MyInt: int`  
  
Typedef  
  
`A`  
  
クラス  
  
ソースの型の図形からターゲットの型の図形にポイントする関連線を描画します。  
  
`Class B {};`  
  
`typedef B MyB;`  
  
`B`  
  
クラス  
  
`MyB : B`  
  
Typedef  
  
typedef の図形を右クリックして **[関連として表示]** をクリックすると、typedef またはクラスと、2 つの図形を結合する**[Alias of]** (エイリアス) の線 (関連線と似ています) が表示されます。  
  
`typedef B MyB;`  
  
`typedef MyB A;`  
  
`MyBar : Bar`  
  
Typedef  
  
上と同じ。  
  
```cpp
Class B {};  
typedef B MyB;  
  
class A {  
   MyB B;  
};  
```  
  
`B`  
  
クラス  
  
`MyB : B`  
  
Typedef  
  
`A`  
  
クラス  
  
`MyB`は入れ子にされた typedef の図形です。  
  
`#include <vector>`  
  
`...`  
  
`using namespace std;`  
  
`...`  
  
`typedef vector<int> MyIntVect;`  
  
`vector<T>`クラス  
  
`MyIntVect : vector<int>`  
  
Typedef  
  
`class B {};`  
  
`typedef B MyB;`  
  
`class A : MyB {};`  
  
`MyB : B`  
  
Typedef  
  
-> B  
  
`B`  
  
`A`  
  
クラス  
  
-> MyB  
  
クラス デザイナーでは、コンテキスト メニュー コマンドを使用したこのような関係の表示はサポートしていません。  
  
`#include <vector>`  
  
`Typedef MyIntVect std::vector<int>;`  
  
`Class MyVect : MyIntVect {};`  
  
`std::vector<T>`  
  
クラス  
  
`MyIntVect : std::vector<int>`  
  
Typedef  
  
`MyVect`  
  
クラス  
  
-> MyIntVect  
  
## <a name="see-also"></a>関連項目
[Visual C++ コードの使用](working-with-visual-cpp-code.md)   
[typedef 指定子](https://msdn.microsoft.com/en-us/library/05w82thz.aspx)