---
title: Win32 のエラー コードを調べるには | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vc.errors
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- error codes, Win32
- Win32, error codes
ms.assetid: 8fb4ff42-b8eb-4152-b49e-b802d194b05e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d2ce767465262533e1122a58bb4c51dd6caf0c5f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53874274"
---
# <a name="where-can-i-look-up-win32-error-codes"></a>Win32 のエラー コードを調べるには
WINERROR.H には、Win32 API 関数のエラー コード定義が含まれています。このファイルは、既定のインストールでは INCLUDE ディレクトリにあります。  
  
 エラー コードを検索するには、[ウォッチ] **ウィンドウまたは [クイック ウォッチ]** ダイアログ ボックスに、検索対象のコードを入力します。 次に例を示します。  
  
`0x80000004,hr` 

  
## <a name="see-also"></a>「  
 [ネイティブ コードのデバッグに関する FAQ](../debugger/debugging-native-code-faqs.md)   
 [ネイティブ コードのデバッグ](../debugger/debugging-native-code.md)