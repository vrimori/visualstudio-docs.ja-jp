---
title: "__value | Microsoft Docs"
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
  - "__value_cpp"
  - "__value"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__value キーワード"
  - "値の型を宣言します。"
  - "_ _value キーワードの構文"
ms.assetid: b14b64f7-5db6-4e92-a144-fcbf67572b49
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __value
> [!NOTE]
>  このトピックは、C\+\+ マネージ拡張のバージョン 1 にのみ対応しています。 この構文は、バージョン 1 のコードを保守するためだけに使用してください。 参照してください [Classes and Structs](/visual-cpp/windows/classes-and-structs-cpp-component-extensions) については、新しい構文で同等の機能を使用します。  
  
 クラスが \_\_value 型であることを宣言します。  
  
## 構文  
  
```  
  
__value  
 class-specifier  
__value  
 struct-specifier  
__nogc  
array-specifier  
__nogc  
pointer-specifier  
  
```  
  
## 解説  
 `__value` 型は、`__gc` 型の変数が直接そのデータを含むのに対し、マネージ変数はそのデータをポイントし、データは共通言語ランタイム ヒープに格納される点が、`__value` とは異なります。  
  
 `__value` 型には次の条件が適用されます。  
  
-   `__value` キーワードをインターフェイスに適用することはできません。  
  
-   `__value` 型は任意の数のインターフェイスから継承でき、その他の型または `__value` 型から継承することはできません。  
  
-   `__value` の型は定義上はシールされています。 詳細については、「[\_\_sealed](../misc/sealed.md)」を参照してください。  
  
-   `__value` 型は、マネージ型が許可される場所であればどこでも使用できます。  
  
> [!NOTE]
>  `__value` キーワードは、`__abstract` キーワードを使用している場合は使用できません。  
  
 `__value` 型は **System::Object** のポインターに明示的に接続できます。 これは、ボックス化と呼ばれます。  
  
 次のガイドラインは、`__nogc` 型の中への値型の埋め込みに適用されます。  
  
-   値型には **LayoutSequential** または **LayoutExplicit** が必要です。  
  
-   値型が gc ポインター メンバーを持つことはできません。  
  
-   値型がプライベート データ メンバーを持つことはできません。  
  
 C\+\+ のマネージ拡張で、C\# のクラスおよび構造体と同等になるものは、次のとおりです。  
  
|C\+\+ マネージ拡張|C\#|詳細情報|  
|------------------|---------|----------|  
|\_\_gc 構造体<br /><br /> または<br /><br /> \_\_gc クラス|クラス|[class](/dotnet/csharp/language-reference/keywords/class) キーワード|  
|\_\_value 構造体<br /><br /> または<br /><br /> \_\_value クラス|struct|[struct](/dotnet/csharp/language-reference/keywords/struct) キーワード|  
  
## 使用例  
 次の例では、`__value` 型 \(`V`\) を宣言し、`__value` 型の 2 つのインスタンスを操作します。  
  
```  
// keyword__value.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
  
__value struct V {   
   int m_i;  
};  
  
int main() {  
   V v1, v2;  
   v1.m_i = 5;  
   v2 = v1;   // copies all fields of v1 to v2  
   v2.m_i = 6;   // does not affect v1.m_I  
}  
```