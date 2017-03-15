---
title: "__abstract | Microsoft Docs"
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
  - "__abstract_cpp"
  - "__abstract"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "抽象クラス [C++]"
  - "__abstract キーワード"
ms.assetid: fc6eee5e-9f07-4438-97f7-f2e124263575
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __abstract
> [!NOTE]
>  このトピックは、C\+\+ マネージ拡張のバージョン 1 にのみ対応しています。 この構文は、バージョン 1 のコードを保守するためだけに使用してください。 参照してください [abstract](/visual-cpp/windows/abstract-cpp-component-extensions) については、新しい構文で同等の機能を使用します。  
  
 直接インスタンス化することができないマネージ クラスを宣言します。  
  
## 構文  
  
```  
  
__abstract   
class-specifier  
__abstract   
struct-specifier  
  
```  
  
## 解説  
 `__abstract` キーワードは、対象クラスが他のクラスの基底クラスとしてのみ使用できることを宣言します。 クラスまたは構造体に `__abstract` を適用することは、結果が \_\_gc クラスまたは \_\_gc 構造体であることを意味しません。  
  
 [抽象](/visual-cpp/cpp/abstract-classes-cpp)基底クラスの C\+\+ の概念とは異なり、`__abstract` キーワードを持つクラスはクラスのメンバー関数を定義できます。  
  
> [!NOTE]
>  `__abstract` キーワードは、`__value` キーワードまたは `__sealed` キーワードを使用している場合は使用できず、`__interface` キーワードを使用している場合は冗長です。  
  
## 使用例  
 次の例では、`Derived` クラスが抽象基底クラス \(`Base`\) から派生します。 その後、両方に対してインスタンス化が試みられますが、`Derived` だけが成功します。  
  
```  
// keyword__abstract.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
  
__abstract __gc class Base {  
   int BaseFunction() {  
      return 0;  
   }  
};  
  
__gc class Derived: public Base {};  
  
int main() {  
   Base* MyBase = new Base();   // C3622 can't BAse is abstract  
   Derived* MyDerived = new Derived();  
}  
```