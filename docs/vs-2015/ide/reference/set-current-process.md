---
title: SetCurrentProcess | Microsoft ドキュメント
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: be451ee1a0b4361e44c8be96713872ca0ee3bd76
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54768849"
---
# <a name="set-current-process"></a>SetCurrentProcess
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
指定されたプロセスをデバッガーでアクティブなプロセスとして設定します。  
  
## <a name="syntax"></a>構文  
  
```  
Debug.SetCurrentProcess index  
```  
  
## <a name="arguments"></a>引数  
 `index`  
 必須です。 プロセスのインデックスです。  
  
## <a name="remarks"></a>コメント  
 デバッグ中には複数のプロセスにアタッチできますが、デバッガーでアクティブになっているプロセスは常に 1 つだけです。 `SetCurrentProcess` コマンドを使用すると、アクティブなプロセスを設定できます。  
  
## <a name="example"></a>例  
  
```  
>Debug.SetCurrentProcess 1  
```  
  
## <a name="see-also"></a>「  
 [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
