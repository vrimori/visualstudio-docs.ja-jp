---
title: "CV_CFL_LANG | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CV_CFL_LANG 列挙型"
ms.assetid: 4e8e0613-ad02-4de9-9f46-e4753c5b0251
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# CV_CFL_LANG
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

アプリケーション モジュールまたはリンク モジュールのソース コード言語を指定します。  
  
## 構文  
  
```cpp#  
typedef enum CV_CFL_LANG {   
   CV_CFL_C       = 0x00,  
   CV_CFL_CXX     = 0x01,  
   CV_CFL_FORTRAN = 0x02,  
   CV_CFL_MASM    = 0x03,  
   CV_CFL_PASCAL  = 0x04,  
   CV_CFL_BASIC   = 0x05,  
   CV_CFL_COBOL   = 0x06,  
   CV_CFL_LINK    = 0x07,  
   CV_CFL_CVTRES  = 0x08,  
   CV_CFL_CVTPGD  = 0x09,  
   CV_CFL_CSHARP  = 0x0A,  
   CV_CFL_VB      = 0x0B,  
   CV_CFL_ILASM   = 0x0C,  
   CV_CFL_JAVA    = 0x0D,  
   CV_CFL_JSCRIPT = 0x0E,  
   CV_CFL_MSIL    = 0x0F,  
   CV_CFL_HLSL    = 0x10  
} CV_CFL_LANG;  
```  
  
## Elements  
 CV\_CFL\_C  
 アプリケーションのは C 言語です。  
  
 CV\_CFL\_CXX  
 アプリケーションの言語は C\+\+ です。  
  
 CV\_CFL\_FORTRAN  
 アプリケーションの言語、FORTRAN です。  
  
 CV\_CFL\_MASM  
 アプリケーションの言語は、Microsoft Macro Assembler です。  
  
 CV\_CFL\_PASCAL  
 アプリケーションの言語は Pascal 形式です。  
  
 CV\_CFL\_BASIC  
 アプリケーションの言語は BASIC です。  
  
 CV\_CFL\_COBOL  
 アプリケーションでは、COBOL 言語です。  
  
 CV\_CFL\_LINK  
 アプリケーションは、リンカーによって生成されたモジュールです。  
  
 CV\_CFL\_CVTRES  
 アプリケーションは、CVTRES ツールによって変換されます。リソース モジュールです。  
  
 CV\_CFL\_CVTPGD  
 アプリケーションは CVTPGD ツールによって生成される POGO に最適化されたモジュールです。  
  
 CV\_CFL\_CSHARP  
 アプリケーションの言語は C\# です。  
  
 CV\_CFL\_VB  
 アプリケーションの言語は Visual Basic です。  
  
 CV\_CFL\_ILASM  
 アプリケーションの言語は中間言語のアセンブリ \(共通言語ランタイムの \(CLR\) のアセンブリ\) です。  
  
 CV\_CFL\_JAVA  
 アプリケーションの言語は、Java です。  
  
 CV\_CFL\_JSCRIPT  
 アプリケーションの言語は、Jscript です。  
  
 CV\_CFL\_MSIL  
 アプリケーションの言語は未知の Microsoft Intermediate Language \(MSIL\)、場合 [\/LTCG \(リンク時のコード生成\)](/visual-cpp/build/reference/ltcg-link-time-code-generation) スイッチを使用した結果です。  
  
 CV\_CFL\_HLSL  
 アプリケーションの言語は Shader の高度な言語です。  
  
## 解説  
 この列挙体の値は [IDiaSymbol::get\_language](../Topic/IDiaSymbol::get_language.md) メソッドの呼び出しによって返されます。  
  
## 必要条件  
 ヘッダー: cvconst.h  
  
## 参照  
 [列挙型と構造体](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_language](../Topic/IDiaSymbol::get_language.md)