---
title: Watch コマンド | Microsoft Docs
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
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9b1d5a1a1ffac1c67b5a3a1e1ad4a860c6b2ad4f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49214358"
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
 必須。 [ウォッチ] ウィンドウのインスタンス番号。  
  
## <a name="remarks"></a>Remarks  
 `index` は整数でなければなりません。 有効値は 1、2、3、または 4 です。  
  
## <a name="example"></a>例  
  
```  
>Debug.Watch1  
```  
  
## <a name="see-also"></a>関連項目  
 [[自動変数] ウィンドウと [ローカル] ウィンドウ](../../debugger/autos-and-locals-windows.md)   
 [方法: 変数ウィンドウで値の編集](http://msdn.microsoft.com/library/36f464ab-c900-4c0b-9ab3-557b3d9cdab5)   
 [方法: [クイック ウォッチ] ダイアログ ボックスを使用します。](http://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867)   
 [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [[検索/コマンド] ボックス](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)



