---
title: List Registers コマンド | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- debug.listregisters
helpviewer_keywords:
- list registers command
- Debug.ListRegisters command
- ListRegisters command
ms.assetid: 19a9d789-f6c9-46b3-b1f6-4934fc33e055
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c9ff1287bb4c92d074c0a0e123d48ddb7e61cc90
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539595"
---
# <a name="list-registers-command"></a>List Registers コマンド
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[レジスタの一覧表示コマンド](https://docs.microsoft.com/visualstudio/ide/reference/list-registers-command)します。  
  
  
選択したレジスタの値を表示するほか、表示されるレジスタの一覧を変更できます。  
  
## <a name="syntax"></a>構文  
  
```  
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]  
[/Watch [{register|registerGroup}...]]  
[/Unwatch [{register|registerGroup}...]]  
```  
  
## <a name="switches"></a>スイッチ  
 /Display [{`register`&#124;`registerGroup`}...]  
 指定した `register` または `registerGroup` の値を表示します。 `register` も `registerGroup` も指定されていない場合は、レジスタの既定の一覧が表示されます。 スイッチが指定されていない場合、動作は同じです。 例えば:  
  
 `Debug.ListRegisters /Display eax`  
  
 上記の式は、次の式と同じです。  
  
 `Debug.ListRegisters eax`  
  
 /List  
 すべてのレジスタ グループが一覧に表示されます。  
  
 /Watch [{`register`&#124;`registerGroup`}...]  
 1 つ以上の `register` または `registerGroup` の値が一覧に追加されます。  
  
 /Unwatch [{`register`&#124;`registerGroup`}...]  
 1 つ以上の `register` または `registerGroup` の値が一覧から削除されます。  
  
## <a name="remarks"></a>Remarks  
 エイリアス `r` を `Debug.ListRegisters` の代わりに使用できます。  
  
## <a name="example"></a>例  
 この例では、`Debug.ListRegisters` のエイリアス `r` を使用して、レジスタ グループ `Flags` の値を表示します。  
  
```  
r /Display Flags  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)   
 [デバッグの基礎 : [レジスタ] ウィンドウ](../../debugger/debugging-basics-registers-window.md)   
 [方法: [レジスタ] ウィンドウを使用する](../../debugger/how-to-use-the-registers-window.md)



