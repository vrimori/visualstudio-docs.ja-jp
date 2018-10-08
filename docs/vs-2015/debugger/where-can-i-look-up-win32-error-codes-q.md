---
title: Win32 のエラー コードを調べるには | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vc.errors
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- error codes, Win32
- Win32, error codes
ms.assetid: 8fb4ff42-b8eb-4152-b49e-b802d194b05e
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 86735dae123d0fdedc59f4205af349b86cc6efd0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47536177"
---
# <a name="where-can-i-look-up-win32-error-codes"></a>Win32 のエラー コードを調べるには
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[できますで Win32 エラー コードを検索しますか?](https://docs.microsoft.com/visualstudio/debugger/where-can-i-look-up-win32-error-codes-q)。  
  
WINERROR.H には、Win32 API 関数のエラー コード定義が含まれています。このファイルは、既定のインストールでは INCLUDE ディレクトリにあります。  
  
 エラー コードを調べるコードを入力して、**ウォッチ**ウィンドウまたは**クイック ウォッチ**  ダイアログ ボックス。 例えば:  
  
```  
0x80000004,hr  
```  
  
## <a name="see-also"></a>関連項目  
 [ネイティブ コードのデバッグに関する Faq](../debugger/debugging-native-code-faqs.md)   
 [ネイティブ コードのデバッグ](../debugger/debugging-native-code.md)



