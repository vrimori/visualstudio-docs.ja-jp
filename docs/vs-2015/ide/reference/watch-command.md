---
title: Watch コマンド | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b1a04dce73dbf2551b51f2395b3512e62daf3766
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54788191"
---
# <a name="watch-command"></a>Watch コマンド
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
指定したインスタンスの **[ウォッチ]** ウィンドウを作成し、開きます。 **[ウォッチ]** ウィンドウを使用すると、変数、式、レジスタの値の計算し、それらの値を編集し、結果を保存することができます。  
  
## <a name="syntax"></a>構文  
  
```  
Debug.Watch[index]  
```  
  
## <a name="arguments"></a>引数  
 `index`  
 必須です。 [ウォッチ] ウィンドウのインスタンス番号。  
  
## <a name="remarks"></a>コメント  
 `index` は整数でなければなりません。 有効値は 1、2、3、または 4 です。  
  
## <a name="example"></a>例  
  
```  
>Debug.Watch1  
```  
  
## <a name="see-also"></a>「  
 [[自動変数] ウィンドウと [ローカル] ウィンドウ](../../debugger/autos-and-locals-windows.md)   
 [方法: [変数] ウィンドウで値を編集します。](http://msdn.microsoft.com/library/36f464ab-c900-4c0b-9ab3-557b3d9cdab5)   
 [方法: [クイック ウォッチ] ダイアログ ボックスを使用します。](http://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867)   
 [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [[検索/コマンド] ボックス](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
