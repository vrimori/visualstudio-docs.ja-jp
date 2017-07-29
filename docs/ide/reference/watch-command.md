---
title: "Watch コマンド | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
caps.latest.revision: 11
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: bf91686a212551ef4b760d5bb2740a14f8495a1b
ms.contentlocale: ja-jp
ms.lasthandoff: 05/24/2017

---
# <a name="watch-command"></a>Watch コマンド
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
  
## <a name="see-also"></a>関連項目  
 [[自動変数] ウィンドウと [ローカル] ウィンドウ](../../debugger/autos-and-locals-windows.md)   
 [Visual Studio でウォッチ ウィンドウとクイック ウォッチ ウィンドウを使用して変数のウォッチ ポイントを設定する](../../debugger/watch-and-quickwatch-windows.md)   
 [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [[検索/コマンド] ボックス](../../ide/find-command-box.md)   
 [Visual Studio コマンドのエイリアス](../../ide/reference/visual-studio-command-aliases.md)
