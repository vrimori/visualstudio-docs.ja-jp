---
title: "CObject から派生したクラスを実装するときのコンパイラ エラー | Microsoft Docs"
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
  - "ソース コードのコンパイル、CObject から派生したクラス"
  - "エラー [C++]"
  - "エラー [C++]、コンパイラ"
  - "CObject クラス、派生クラスのコンパイラ エラー"
ms.assetid: 9f249b52-aeff-41a1-8a74-a52aa08c4fcf
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CObject から派生したクラスを実装するときのコンパイラ エラー
`CObject` から派生したクラスを実装し、そのクラスのコピー コンストラクターまたは代入演算子を呼び出す必要があるようにコードが記述されている場合、コンパイラは、次のようなエラーを報告することがあります。  
  
```  
error C2660: 'CSample::CSample' : function does not take 1 parameters error C2582: 'CSample' : 'operator =' function is unavailable  
```  
  
 後述の「サンプル コード」セクションの例をコンパイルすることで、この問題を再現することができます。  
  
> [!NOTE]
>  この記事で示したサンプル コードでは、次のエラー メッセージが生成されます。  
  
```  
error C2558: 'CSample::CSample' : no copy constructor available error C2582: 'CSample' : 'operator =' function is unavailable  
```  
  
 コンパイラ エラーの原因は、`CObject` が AFX.h ファイルでプライベート コピー コンストラクターと代入演算子を宣言していることです。 そのため、`CObject` から派生したクラスの既定のコピー コンストラクターと代入演算子がコンパイラによって生成されません。 コンパイラはクラスで宣言されているこれらの関数を検出できないため、エラーを報告します。  
  
 コンパイラ エラーを回避するには、`CObject` から派生したクラスのコピー コンストラクターと代入演算子を実装する必要があります。 これを次のサンプル コードに示します。 サンプル コードに示された行のコメントを解除して、エラーを回避できます。  
  
## サンプル コード  
  
```  
// _error_Compiler_Errors_when_Implementing_a_CObject.2d.Derived_Class.cpp /* Compile options needed: /c */ // replace with #define _CONSOLE when compiling for Windows NT #define _DOS #include <afx.h> class CSample : public CObject { private: short m_nValue; public: // uncomment the lines below to avoid the compiler errors //    CSample() {} //    CSample( const CSample &s )  // copy ctor //        { m_nValue = s.m_nValue; } //    CSample& operator=( const CSample &s )  // assignment operator //        { m_nValue = s.m_nValue; return *this; } }; int main() { CSample a; CSample b = a; a = b; }  
  
```  
  
## 参照  
 [コンパイラの警告s C4600 Through C4999](/visual-cpp/error-messages/compiler-warnings/compiler-warnings-c4600-through-c4799)