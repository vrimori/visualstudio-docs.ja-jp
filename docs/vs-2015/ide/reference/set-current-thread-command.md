---
title: SetCurrentThread コマンド | Microsoft ドキュメント
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- debug.setcurrentthread
helpviewer_keywords:
- Set Current Thread command
- Debug.SetCurrentThread command
ms.assetid: 9917ed1d-6c30-4d94-b2f0-69acce74f1b2
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 406a89a228483568c779e32410b005e7c16d7323
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49266815"
---
# <a name="set-current-thread-command"></a>SetCurrentThread コマンド
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
指定したスレッドを現在のスレッドとして設定します。  
  
## <a name="syntax"></a>構文  
  
```  
Debug.SetCurrentThread index  
```  
  
## <a name="arguments"></a>引数  
 `index`  
 必須。 スレッドをそのインデックスで選択します。  
  
## <a name="example"></a>例  
  
```  
>Debug.SetCurrentThread 1  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [[検索/コマンド] ボックス](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)



