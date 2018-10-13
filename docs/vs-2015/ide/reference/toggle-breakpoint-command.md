---
title: ToggleBreakpoint コマンド | Microsoft Docs
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
- debug.togglebreakpoint
helpviewer_keywords:
- ToggleBreakpoint command
- Debug.ToggleBreakPoint command
- Toggle Breakpoint command
ms.assetid: d50dfadb-ce79-4d5e-9c09-1cfddd57876d
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f993d9a0377531b155301bed235c00bf8e6667c4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49223159"
---
# <a name="toggle-breakpoint-command"></a>ToggleBreakpoint コマンド
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
ファイル内の現在位置で、現在の状態に基づいてブレークポイントのオン/オフを切り替えます。  
  
## <a name="syntax"></a>構文  
  
```  
Debug.ToggleBreakpoint [text]  
```  
  
## <a name="arguments"></a>引数  
 `text`  
 任意。 テキストを指定すると、行が名前付きのブレークポイントとしてマークされます。 それ以外の場合は、行は名前のないブレークポイントとしてマークされ、これは F9 キーを押したときの動作に似ています。  
  
## <a name="example"></a>例  
 次の例では、現在のブレークポイントを切り替えます。  
  
```  
>Debug.ToggleBreakpoint  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [[検索/コマンド] ボックス](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)



