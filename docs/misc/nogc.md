---
title: "__nogc | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__nogc_cpp"
  - "__nogc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__nogc 型の宣言"
  - "アンマネージ型のクラス [C++]"
  - "アンマネージ クラスの宣言"
  - "アンマネージ クラス"
ms.assetid: 3e7f1b09-0fc3-4a8f-9458-a22f7a38ce45
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __nogc
> [!NOTE]
>  このトピックは、C\+\+ マネージ拡張のバージョン 1 にのみ対応しています。 この構文は、バージョン 1 のコードを保守するためだけに使用してください。 新しい構文では、明示的にアンマネージ型を指定する必要はありません。  
  
 アンマネージ型を明示的に宣言します。  
  
## 構文  
  
```  
  
__nogc   
class-specifier  
__nogc   
struct-specifier  
__nogc  
interface-specifier  
__nogc  
array-specifier  
__nogc  
pointer-specifier  
__nogc  
new  
  
```  
  
## 解説  
 `__nogc` キーワードは、オブジェクトが標準 C\+\+ ヒープに割り当てられることを明示的に指定するために使用されます。 このキーワードは省略可能です。 クラス宣言の前に `__gc` または `__nogc` を指定しない場合、既定では `__nogc` が設定されます。  
  
 この型のオブジェクトは、標準 C\+\+ ヒープから割り当てられ、マネージ オブジェクトの制限を受けないという点で、標準 C\+\+ オブジェクトに似ています。  
  
 `__nogc` キーワードは、\_\_value の型のオブジェクトが標準 C\+\+ ヒープに明示的に割り当てられている場合に使用されます。  
  
```  
// keyword__nogc.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
__value struct V {   
   int i;  
};  
int main() {  
   V * v = __nogc new V;  
   v->i = 10;  
   delete v;  
}  
```  
  
> [!NOTE]
>  `__nogc` キーワードは、配列型とポインター型にも適用できます。  
  
 gc ポインターを `__nogc` クラスのメンバーにすることはできません。`__nogc` クラスへの値型の埋め込みに関するガイドラインについては、「[\_\_value](../misc/value.md)」を参照してください。  
  
## 使用例  
 次の例では、アンマネージ クラス \(`X`\) が宣言され、オブジェクトがインスタンス化され、変更されています。  
  
```  
// keyword__nogc_2.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
__nogc class X {  
public:  
   int i;  
};  
  
int main() {  
   X* x;   // declares an unmanaged pointer of type X  
   x = new X();   // creates unmanaged object of type X on the C++ heap  
   Console::WriteLine(x->i);  
  
   x->i = 4;   // modifies unmanaged object  
   Console::WriteLine(x->i);  
  
   delete x;   // call C++ delete operator to clean up resource  
}  
```  
  
 **48378256 4**