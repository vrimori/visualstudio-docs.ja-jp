---
title: "配列の共変性 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "配列 [C++]、ジェネリックの共変性"
ms.assetid: 889fdde3-85fe-44d5-bf2d-d3d4aa14e746
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "mithom"
manager: "douge"
---
# 配列の共変性
直接的または間接的な基底クラス B を持つ参照クラス D を指定するには、D 型の配列を変数に割り当てられる、配列タイプ b の  
  
```  
// clr_array_covariance.cpp  
// compile with: /clr  
using namespace System;  
  
int main() {  
   // String derives from Object  
   array<Object^>^ oa = gcnew array<String^>(20);  
}  
```  
  
## 解説  
 配列の要素への代入は代入互換性をでなければいけない配列の動的な型を使用します。 互換性のない型である配列要素への代入には、スローされる System::ArrayTypeMismatchException が発生します。  
  
 配列の共変性は、値クラス型の配列には適用されません。 たとえば、int32 型の配列をオブジェクトに変換できない ^ ボックス化を使用しても、配列。  
  
## 使用例  
  
```  
// clr_array_covariance2.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct Base { int i; };  
ref struct Derived  : Base {};  
ref struct Derived2 : Base {};  
ref struct Derived3 : Derived {};  
ref struct Other { short s; };  
  
int main() {  
   // Derived* d[] = new Derived*[100];  
   array<Derived^> ^ d = gcnew array<Derived^>(100);  
  
   // ok by array covariance  
   array<Base ^> ^  b = d;  
  
   // invalid  
   // b[0] = new Other;  
  
   // error (runtime exception)  
   // b[1] = gcnew Derived2;  
  
   // error (runtime exception),  
   // must be "at least" a Derived.  
   // b[0] = gcnew Base;  
  
   b[1] = gcnew Derived;  
   b[0] = gcnew Derived3;  
}  
```  
  
## 参照  
 [Arrays](/visual-cpp/windows/arrays-cpp-component-extensions)