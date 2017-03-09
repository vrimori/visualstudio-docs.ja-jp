---
title: "コンパイラ エラー CS0021 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0021"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0021"
ms.assetid: 4eb5fa24-8261-4962-b36a-224be5074217
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0021
角かっこ \[\] 付きインデックスを 'type' 型の式に適用することはできません  
  
 [インデクサー](/dotnet/csharp/programming-guide/indexers/index) をサポートしないデータ型に対し、インデクサーによって値にアクセスしようとしました。  
  
 C\+\+ アセンブリでインデクサーの使用を試行すると、CS0021 エラーが発生することがあります。 この場合は、既定のインデクサーを C\# コンパイラが判別できるように、C\+\+ クラスを `DefaultMember` 属性で修飾します。 次の例では CS0021 エラーが生成されます。  
  
## 使用例  
 エラーを生成するには、このファイルをコンパイルして \(`DefaultMember` 属性をコメント アウトして\) .dll ファイルを作成します。  
  
```  
// CPP0021.cpp // compile with: /clr /LD using namespace System::Reflection; // Uncomment the following line to resolve //[DefaultMember("myItem")] public ref class MyClassMC { public: property int myItem[int] { int get(int i){  return 5; } void set(int i, int value) {} } };  
```  
  
## 使用例  
 次のコードは .dll ファイルを呼び出す C\# ファイルです。 このファイルはインデクサーを経由してクラスへのアクセスを試行しますが、既定のインデクサーとして宣言されたメンバーが存在しないため、エラーが生成されます。  
  
```  
// CS0021.cs // compile with: /reference:CPP0021.dll public class MyClass { public static void Main() { MyClassMC myMC = new MyClassMC(); int j = myMC[1]; // CS0021 } }  
```