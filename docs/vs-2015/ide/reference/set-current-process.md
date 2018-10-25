---
title: SetCurrentProcess | Microsoft ドキュメント
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0baea39c341e8034ff222de32548d0518f115e82
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49246663"
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
 必須。 プロセスのインデックスです。  
  
## <a name="remarks"></a>Remarks  
 デバッグ中には複数のプロセスにアタッチできますが、デバッガーでアクティブになっているプロセスは常に 1 つだけです。 `SetCurrentProcess` コマンドを使用すると、アクティブなプロセスを設定できます。  
  
## <a name="example"></a>例  
  
```  
>Debug.SetCurrentProcess 1  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)



