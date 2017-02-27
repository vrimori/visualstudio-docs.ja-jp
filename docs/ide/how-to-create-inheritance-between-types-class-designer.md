---
title: "How to: Create Inheritance Between Types (Class Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.classdesigner.inheritanceline"
helpviewer_keywords: 
  - "inheritance, relationship defining"
  - "relationships, defining inheritance"
ms.assetid: 3786a21c-8022-4bf5-9d13-740fd354e93c
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 30
---
# How to: Create Inheritance Between Types (Class Designer)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

クラス デザイナーを使用してクラス ダイアグラム上の 2 つの型間の継承関係を作成するには、基本型をその派生型 \(複数可\) に接続します。  継承関係は、2 つのクラス間、クラスとインターフェイス間、または 2 つのインターフェイス間で作成できます。  
  
### 型間で継承を作成するには  
  
1.  ソリューション エクスプローラーのプロジェクトから、クラス ダイアグラム \(.cd\) ファイルを開きます。  
  
     クラス ダイアグラムがない場合は、クラス ダイアグラムを作成します。  「[How to: Add Class Diagrams to Projects \(Class Designer\)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)」を参照してください。  
  
2.  **\[クラス デザイナー\]** の **\[ツールボックス\]** で、**\[継承\]** をクリックします。  
  
3.  クラス ダイアグラムで、必要な型間の継承線を次の間で描画します。  
  
    -   派生クラスから基底クラスへ  
  
    -   実装するクラスから実装されるインターフェイスへ  
  
    -   拡張するインターフェイスから拡張されるインターフェイスへ  
  
4.  必要に応じて、ジェネリック型からの派生型がある場合に、継承線をクリックします。  **\[プロパティ\]** ウィンドウで、**\[型の引数\]** プロパティをジェネリック型に必要な型と一致するように設定します。  
  
    > [!NOTE]
    >  親抽象クラスに少なくとも 1 つの抽象メンバーが含まれている場合、すべての抽象メンバーは非抽象継承クラスとして実装されます。  「[Implementing Abstract Base Classes](../ide/refactoring-classes-and-types-class-designer.md#ImplementingAbstractBaseClasses)」を参照してください。  
    >   
    >  既存のジェネリック型を視覚化できますが、新しいジェネリック型は作成できません。  また、既存のジェネリック型の型パラメーターは変更できません。  
  
## 参照  
 [継承](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)   
 [Inheritance Basics](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)   
 [How to: View Inheritance Between Types \(Class Designer\)](../ide/how-to-view-inheritance-between-types-class-designer.md)   
 [Visual C\+\+ Classes in Class Designer](../ide/visual-cpp-classes-in-class-designer.md)