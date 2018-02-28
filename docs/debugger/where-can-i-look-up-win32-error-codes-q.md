---
title: "Win32 のエラー コードを調べるには | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: f48f3fbff8f7f18fa745df7ac9571c69038651e6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="where-can-i-look-up-win32-error-codes"></a>Win32 のエラー コードを調べるには
WINERROR.H には、Win32 API 関数のエラー コード定義が含まれています。このファイルは、既定のインストールでは INCLUDE ディレクトリにあります。  
  
 コードを入力して、エラー コードを検索できます、**ウォッチ**ウィンドウまたは**クイック ウォッチ**  ダイアログ ボックス。 例:  
  
```  
0x80000004,hr  
```  
  
## <a name="see-also"></a>参照  
 [ネイティブ コードのデバッグに関する Faq](../debugger/debugging-native-code-faqs.md)   
 [ネイティブ コードのデバッグ](../debugger/debugging-native-code.md)