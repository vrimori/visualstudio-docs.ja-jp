---
title: "__typeof | Microsoft Docs"
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
  - "__typeof_cpp"
  - "__typeof"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - " __typeof キーワード"
ms.assetid: d71b9603-35d0-4c62-b5b4-90ffc2305a55
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __typeof
メモ   このトピックは、C\+\+ マネージ拡張のバージョン 1 にのみ対応しています。 この構文は、バージョン 1 のコードを保守するためだけに使用してください。 参照してください [typeid](/visual-cpp/windows/typeid-cpp-component-extensions) については、新しい構文で同等の機能を使用します。  
  
 指定された型の **System::Type** を返します。  
  
```  
  
__typeof(  
typename  
)  
  
```  
  
 それぞれの文字について以下に説明します。  
  
 *typename*  
 **System::Type** の名前を必要とするマネージ型の名前。 マネージ プログラムでは、ネイティブ型は一部、共通言語ランタイムの型にエイリアスされることに注意してください。 たとえば、`int` は **System::Int32** のエイリアスです。  
  
## 解説  
 **\_\_typeof** 演算子を使用すると、指定した型の **System::Type** 型を取得できます。 また、**\_\_typeof** を使用して、カスタム属性ブロックの **System::Type** の値を返すこともできます。 独自属性の作成方法の詳細については、「[attribute](/visual-cpp/windows/attribute)」を参照してください。  
  
## 使用例  
 次の例では、カスタム属性 \(`AtClass`\) は、\_\_gc クラス \(`B`\) に適用されます。 カスタム属性の値は **\_\_typeof** で取得されます。  
  
```  
// keyword__typeof.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
public __gc class MyClass {};  
  
[attribute(All)]  
__gc class AtClass {  
public:  
   AtClass(Type*) {  
      Console::WriteLine("in Type * constructor");  
   }  
  
   AtClass(String*) {}  
   AtClass(int) {}  
};  
  
[AtClass(__typeof(MyClass))]   // Apply AtClass attribute to class B  
__gc class B {};  
  
int main() {  
   Type * mytype = __typeof(B);  
   Object * myobject __gc[] = mytype -> GetCustomAttributes(true);  
   Console::WriteLine(myobject[0]);  
}  
```  
  
## 出力  
  
```  
in Type * constructor  
AtClass  
```