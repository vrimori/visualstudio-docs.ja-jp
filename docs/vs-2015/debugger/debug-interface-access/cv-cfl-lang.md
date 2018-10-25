---
title: CV_CFL_LANG |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- CV_CFL_LANG enumeration
ms.assetid: 4e8e0613-ad02-4de9-9f46-e4753c5b0251
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 269953e2e6d7aaca4d6b152e9e7a2cfb00b52573
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49857745"
---
# <a name="cvcfllang"></a>CV_CFL_LANG
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

アプリケーションまたはリンクされているモジュールのソース コードの言語を指定します。  
  
## <a name="syntax"></a>構文  
  
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
  
## <a name="elements"></a>Elements  
 CV_CFL_C  
 アプリケーションの言語は C です。  
  
 CV_CFL_CXX  
 アプリケーションの言語は C++ です。  
  
 CV_CFL_FORTRAN  
 アプリケーションの言語では、FORTRAN です。  
  
 CV_CFL_MASM  
 アプリケーションの言語では、Microsoft Macro Assembler です。  
  
 CV_CFL_PASCAL  
 アプリケーションの言語は、pascal 形式です。  
  
 CV_CFL_BASIC  
 アプリケーションの言語には BASIC です。  
  
 CV_CFL_COBOL  
 アプリケーションの言語では、COBOL です。  
  
 CV_CFL_LINK  
 アプリケーションは、リンカーによって生成されたモジュールです。  
  
 CV_CFL_CVTRES  
 アプリケーションは、リソース モジュールが CVTRES ツールを使用して変換です。  
  
 CV_CFL_CVTPGD  
 アプリケーションは、CVTPGD ツールで生成された最適化 POGO モジュールです。  
  
 CV_CFL_CSHARP  
 アプリケーションの言語は c# です。  
  
 CV_CFL_VB  
 アプリケーションの言語とは、Visual Basic です。  
  
 CV_CFL_ILASM  
 アプリケーションの言語は、中間言語アセンブリ (つまり、共通言語ランタイム (CLR) アセンブリ) です。  
  
 CV_CFL_JAVA  
 Java は、アプリケーションの言語です。  
  
 CV_CFL_JSCRIPT  
 アプリケーションの言語では、Jscript です。  
  
 CV_CFL_MSIL  
 アプリケーションの言語は、不明な Microsoft 中間言語 (MSIL)、結果を使用する可能性があります、 [/LTCG (リンク時コード生成)](http://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2)スイッチします。  
  
 CV_CFL_HLSL  
 アプリケーションの言語は、High Level Shader Language です。  
  
## <a name="remarks"></a>Remarks  
 この列挙体の値が呼び出しによって返される、 [idiasymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)メソッド。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: cvconst.h  
  
## <a name="see-also"></a>関連項目  
 [列挙体と構造体](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)



