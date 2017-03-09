---
title: "__property | Microsoft Docs"
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
  - "__property_cpp"
  - "__property"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__property キーワード"
  - "マネージ クラス"
  - "クラスのマネージ プロパティ [C++]"
ms.assetid: 235e3574-6882-4c52-8301-270277b9216d
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __property
> [!NOTE]
>  このトピックは、C\+\+ マネージ拡張のバージョン 1 にのみ対応しています。 この構文は、バージョン 1 のコードを保守するためだけに使用してください。 参照してください [property](/visual-cpp/windows/property-cpp-component-extensions) については、新しい構文で同等の機能を使用します。  
  
 マネージ クラスのスカラー プロパティまたはインデックス付きプロパティを宣言します。  
  
## 構文  
  
```  
  
__property  
function-declarator  
  
```  
  
## 解説  
 `__property` キーワードは、プロパティの宣言を導入し、クラス、インターフェイス、または値型で使用できます。 プロパティには getter 関数 \(読み取り専用\)、setter 関数 \(書き込み専用\)、またはその両方 \(読み取り\/書き込み\) を定義できます。  
  
> [!NOTE]
>  プロパティ名は、それを含むマネージ クラスの名前と同じにすることはできません。 getter 関数の戻り値の型は、対応する setter 関数の最後のパラメーターの型と一致する必要があります。  
  
## 使用例  
 次の例では、スカラー プロパティ \(`Size`\) を `MyClass` 宣言に追加しています。 プロパティは `get_Size` 関数と `set_Size` 関数を使用して暗黙的に設定および検索されます:  
  
```  
// keyword__property.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
__gc class MyClass {  
public:  
   MyClass() : m_size(0) {}  
   __property int get_Size() { return m_size; }  
   __property void set_Size(int value) { m_size = value; }  
   // compiler generates pseudo data member called Size  
protected:  
   int m_size;  
};  
  
int main() {  
   MyClass* class1 = new MyClass;  
   int curValue;  
  
   Console::WriteLine(class1->Size);  
  
   class1->Size = 4;   // calls the set_Size function with value==4  
   Console::WriteLine(class1->Size);  
  
   curValue = class1->Size;   // calls the get_Size function  
   Console::WriteLine(curValue);  
}  
```  
  
## 出力  
  
```  
0  
4  
4  
```