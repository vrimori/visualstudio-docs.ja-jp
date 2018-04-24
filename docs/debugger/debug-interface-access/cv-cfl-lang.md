---
title: CV_CFL_LANG |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_CFL_LANG enumeration
ms.assetid: 4e8e0613-ad02-4de9-9f46-e4753c5b0251
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c383fd188c035dfacf41cdf86a84b4afe8dfa40d
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="cvcfllang"></a>CV_CFL_LANG
アプリケーションまたはリンクされたモジュールのソース コードの言語を指定します。  
  
## <a name="syntax"></a>構文  
  
```C++  
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
  
## <a name="elements"></a>Elements  
 CV_CFL_C  
 アプリケーションの言語は C.  
  
 CV_CFL_CXX  
 アプリケーションの言語は C++ です。  
  
 CV_CFL_FORTRAN  
 アプリケーションの言語は、FORTRAN です。  
  
 CV_CFL_MASM  
 アプリケーションの言語は、Microsoft マクロ アセンブラーです。  
  
 CV_CFL_PASCAL  
 アプリケーションの言語は、pascal 形式です。  
  
 CV_CFL_BASIC  
 アプリケーションの言語は BASIC です。  
  
 CV_CFL_COBOL  
 アプリケーションの言語は、COBOL です。  
  
 CV_CFL_LINK  
 アプリケーションは、リンカーによって生成されたモジュールです。  
  
 CV_CFL_CVTRES  
 アプリケーションは、リソース モジュール CVTRES ツールを使用して変換されます。  
  
 CV_CFL_CVTPGD  
 アプリケーションは、CVTPGD ツールで生成された最適化 POGO モジュールです。  
  
 CV_CFL_CSHARP  
 アプリケーションの言語は c# です。  
  
 CV_CFL_VB  
 アプリケーションの言語とは、Visual Basic です。  
  
 CV_CFL_ILASM  
 アプリケーションの言語は、中間言語アセンブリ (つまり、共通言語ランタイム (CLR) アセンブリ) です。  
  
 CV_CFL_JAVA  
 アプリケーションの言語は、Java です。  
  
 CV_CFL_JSCRIPT  
 アプリケーションの言語は、Jscript です。  
  
 CV_CFL_MSIL  
 アプリケーションの言語は、不明な Microsoft Intermediate Language (MSIL) の結果を使用する可能性があります、 [/LTCG (リンク時コード生成)](/cpp/build/reference/ltcg-link-time-code-generation)スイッチします。  
  
 CV_CFL_HLSL  
 アプリケーションの言語は、高レベルのシェーダー言語です。  
  
## <a name="remarks"></a>コメント  
 この列挙体の値がへの呼び出しによって返される、 [idiasymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)メソッドです。  
  
## <a name="requirements"></a>要件  
 ヘッダー: cvconst.h  
  
## <a name="see-also"></a>関連項目  
 [列挙体と構造体](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)