---
title: "__sealed | Microsoft Docs"
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
  - "__sealed_cpp"
  - "__sealed"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "sealed キーワード [C++]"
  - "__sealed キーワード"
ms.assetid: 9e5f778a-4ad8-468d-9c44-783e576fb49b
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __sealed
> [!NOTE]
>  このトピックは、C\+\+ マネージ拡張のバージョン 1 にのみ対応しています。 この構文は、バージョン 1 のコードを保守するためだけに使用してください。 参照してください [sealed](/visual-cpp/windows/sealed-cpp-component-extensions) については、新しい構文で同等の機能を使用します。  
  
 メソッドがオーバーライドされたり、クラスが基底クラスになったりすることを防ぎます。  
  
## 構文  
  
```  
  
__sealed   
class-specifier  
__sealed   
struct-specifier  
__sealed   
function-declarator  
  
```  
  
## 解説  
 `__sealed` キーワードは、クラス メソッドをオーバーライドできないこと、またはクラスを基底クラスにできないことを指定します。  
  
 `__sealed` キーワードを使用する場合は、次の点に注意してください。  
  
-   `__sealed` 仮想メソッドはオーバーライドできません。  
  
-   非仮想メンバー メソッドが `__sealed` でマークされている場合、`__sealed` 修飾子は無視されます。  
  
-   `__sealed` メソッドは純粋にはできません。  
  
-   **\_ \_Sealed** を使用すると、キーワードは使用できませんが、 [\_ \_interface](/visual-cpp/cpp/interface) キーワードです。  
  
 クラス \(または構造体\) が `__sealed` でマークされると、そのクラスは基底クラスとして使用できません。 例:  
  
```  
__sealed __gc class A {  
   // ...  
};  
// error: cannot derive from a sealed class  
__gc class B : public A { /* ...*/ };  
```  
  
> [!NOTE]
>  `__sealed` キーワードは、`__abstract` キーワードを使用している場合は使用できません。  
  
## 使用例  
 次の例では、シールされた仮想メソッド \(`f`\) が宣言されています。 関数は `main()` によってオーバーライドされ、コンパイラ エラーが発生します。  
  
```  
// keyword__sealed.cpp  
// compile with: /clr:oldSyntax  
  
#using <mscorlib.dll>  
extern "C" int printf_s(const char*, ...);  
  
__gc struct I  
{  
    __sealed virtual void f()  
    {   
        printf_s("I::f()\n");   
    }  
    virtual void g()  
    {  
        printf_s("I::g()\n");  
    }  
};  
  
__gc struct A : I   
{  
    void f() // C3248 sealed function  
    {   
        printf_s("A::f()\n");   
    }     
    void g()  
    {  
        printf_s("A::g()\n");  
    }  
};  
  
int main()  
{  
    A* pA = new A;  
  
    pA->f();  
    pA->g();  
}  
```