---
title: "__box | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__box"
  - "__box_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__box キーワード"
  - "ボックス化"
  - "ボックス化解除"
  - "ボックス化、_ _box キーワード"
ms.assetid: 935b4a4d-fc45-484c-87c6-d95cfc67cc9d
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __box
> [!NOTE]
>  このトピックは、C\+\+ マネージ拡張のバージョン 1 にのみ対応しています。 この構文は、バージョン 1 のコードを保守するためだけに使用してください。 参照してください [Boxing](/visual-cpp/windows/boxing-cpp-component-extensions) については、新しい構文で同等の機能を使用します。  
  
 \_\_value クラスのオブジェクトのマネージ コピーを作成します。  
  
## 構文  
  
```  
  
__box(  
value-class identifier  
)  
  
```  
  
## 解説  
 `__box` キーワードは、既存の \_\_value クラスのオブジェクトからマネージ オブジェクト \(**System::ValueType** から派生するオブジェクト\) を作成するために使用されます。`__box` キーワードを \_\_value クラスに適用すると、次の処理が実行されます。  
  
-   マネージ オブジェクトが共通言語ランタイム ヒープに割り当てられます。  
  
-   \_\_value クラスのオブジェクトの現在の値が、マネージ オブジェクトにビット単位でコピーされます。  
  
-   新しいマネージ オブジェクトのアドレスが返されます。  
  
 このプロセスをボックス化と呼びます。 ボックス化を実行すると、**System::ValueType** が **System::Object** を継承した結果、マネージ オブジェクトが間接的に **System::Object** を継承するため、マネージ オブジェクトに対して動作するジェネリック ルーチンで、任意の \_\_value クラスのオブジェクトを使用できます。  
  
> [!NOTE]
>  新しく作成したボックス化されたオブジェクトは、\_\_value クラスのオブジェクトのコピーです。 したがって、ボックス化されたオブジェクトの値を変更しても、\_\_value クラス オブジェクトの内容には影響を与えません。  
  
## 使用例  
 ボックス化とボックス化解除の例を次に示します。  
  
```  
// keyword__box.cpp  
// compile with: /clr:oldSyntax  
#using < mscorlib.dll >  
using namespace System;  
  
int main() {  
  Int32 i = 1;  
  System::Object* obj = __box(i);  
  Int32 j = *dynamic_cast<__box Int32*>(obj);  
}  
```  
  
 次の例では、アンマネージ値の型 \(`V`\) がボックス化され、マネージ パラメーターとして `Positive` 関数に渡されています。  
  
```  
// keyword__box2.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
__value struct V {  
   int i;  
};  
void Positive(Object*) {}   // expects a managed class  
  
int main() {  
   V v={10};   // allocate and initialize  
   Console::WriteLine(v.i);  
  
   // copy to the common language runtime heap  
   __box V* pBoxedV = __box(v);  
   Positive(pBoxedV);   // treat as a managed class  
  
   pBoxedV->i = 20;   // update the boxed version  
   Console::WriteLine(pBoxedV->i);  
}  
```  
  
 **10 20**