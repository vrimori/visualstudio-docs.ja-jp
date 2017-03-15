---
title: "How to: Create Types by using Class Designer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.Clr.ClrAttributesDialog"
helpviewer_keywords: 
  - "custom attributes, applying"
  - "class diagrams, creating types"
  - "classes [Visual Studio], creating with Class Designer"
  - "Class Designer [Visual Studio], creating classes"
  - "types [Visual Studio], class diagrams"
  - "attributes [Visual Studio], applying custom"
ms.assetid: 94458c31-28bc-40e2-9737-85868788a0e5
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# How to: Create Types by using Class Designer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual C\# .NET プロジェクトおよび Visual Basic .NET プロジェクトの新しい型を設計するには、これらをクラス ダイアグラム上で作成します。  既存の型を表示するには、「[How to: View Existing Types \(Class Designer\)](../Topic/How%20to:%20View%20Existing%20Types%20\(Class%20Designer\).md)」を参照してください。  
  
-   [新しい型の作成](#CreateType)  
  
-   [カスタム属性を型に適用する](#CustAttributeType)  
  
-   [カスタム属性を型のメンバーに適用する](#CustAttributeMember)  
  
##  <a name="CreateType"></a> 新しい型の作成  
  
1.  クラス デザイナーのツールボックスから、いずれかをクラス ダイアグラムにドラッグします。  
  
    -   **\[クラス\]** または **\[抽象クラス\]**  
  
    -   **Enum**  
  
    -   **Interface**  
  
    -   **\[構造体\]** \(VB\) または **\[構造体\]** \(C\#\)  
  
    -   **Delegate**  
  
    -   **\[モジュール**\] \(VB のみ\)  
  
2.  型の名前を付けます。  それからアクセス レベルを選択します。  
  
3.  型の初期コードを追加するファイルを選択します。  
  
    -   新しいクラス ファイルを作成して、そのファイルを現在のプロジェクトに追加するには、**\[新しいファイルの作成\]** をクリックし、ファイル名を入力します。  
  
    -   既存のファイルにコードを追加するには、**\[存在するファイルに追加\]** をクリックします。  
  
         ソリューションに複数のアプリでコードを共有しているプロジェクトがある場合、対応するクラス ファイルが同じアプリ プロジェクトまたは共有プロジェクトにある場合にのみ、アプリケーション プロジェクトで新しい型をクラス ダイアグラムに追加できます。  
  
4.  次に、型を定義するために他の項目を追加します。  
  
    |||  
    |-|-|  
    |**For**|**追加**|  
    |クラス、抽象クラス、構造体|型を定義するメソッド、プロパティ、フィールド、イベント、コンストラクター \(メソッド\)、デストラクター \(メソッド\)、および定数|  
    |列挙型|列挙型を構成するフィールド値|  
    |インターフェイス|インターフェイスを構成するメソッド、プロパティ、イベント|  
    |Delegate|デリゲートを定義するパラメーター|  
    |Module|モジュールを定義するメソッド、プロパティ、フィールド、イベント、コンストラクター \(メソッド\)、および定数|  
  
     「[メンバーの作成](../ide/creating-and-configuring-type-members-class-designer.md#CreateMembers)」を参照してください。  
  
##  <a name="CustAttributeType"></a> カスタム属性を型に適用する  
  
1.  クラス ダイアグラムで型の図形をクリックします。  
  
2.  \[プロパティ\] ウィンドウで、型の **\[カスタム属性\]** プロパティの横の省略記号 \(...\) ボタンをクリックします。  
  
3.  1 つ以上のカスタム属性を 1 行あたり 1 つ追加します。  角かっこで閉じません。  
  
     終了後、カスタム属性が型に適用されます。  
  
##  <a name="CustAttributeMember"></a> カスタム属性を型のメンバーに適用する  
  
1.  クラス ダイアグラムの型の図形でメンバーの名前をクリックするか、\[クラスの詳細\] ウィンドウでその行をクリックします。  
  
2.  \[プロパティ\] ウィンドウで、メンバーの **\[カスタム属性\]** プロパティを探します。  
  
3.  1 つ以上のカスタム属性を 1 行あたり 1 つ追加します。  角かっこで閉じません。  
  
     終了後、カスタム属性が型に適用されます。  
  
## 参照  
 [How to: Create Inheritance Between Types \(Class Designer\)](../ide/how-to-create-inheritance-between-types-class-designer.md)   
 [How to: Create Associations Between Types \(Class Designer\)](../ide/how-to-create-associations-between-types-class-designer.md)   
 [Creating and Configuring Type Members \(Class Designer\)](../ide/creating-and-configuring-type-members-class-designer.md)   
 [Working with Class Diagrams \(Class Designer\)](../ide/working-with-class-diagrams-class-designer.md)   
 [Designing Classes and Types \(Class Designer\)](../ide/designing-classes-and-types-class-designer.md)