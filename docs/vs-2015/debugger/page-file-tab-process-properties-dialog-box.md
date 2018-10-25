---
title: ページファイル タブの プロセス プロパティ ダイアログ ボックス |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: daf41a06-8a55-48f6-95f5-49a8416bd308
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c3394d2b71fad7b9d611bc4392f55d4518766665
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49209340"
---
# <a name="page-file-tab-process-properties-dialog-box"></a>[ページ ファイル] タブ ([プロセス プロパティ] ダイアログ ボックス)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

使用して、**ページファイル**タブ プロセスのページング ファイルを確認します。 表示する、[プロセス プロパティ ダイアログ ボックス](../debugger/process-properties-dialog-box.md)、フォーカスを移動、[プロセス ビュー](../debugger/processes-view.md)ウィンドウ。 ツリーで、プロセスの任意のノードを選択し、**プロパティ**から、**ビュー**メニュー。  
  
 次の設定は [使用可能な**ページファイル**] タブ。  
  
|入力|説明|  
|-----------|-----------------|  
|**ページファイルのサイズ**|ページング ファイル内でこのプロセスを使用しているページの現在数。 ページング ファイルには、ページのプロセスによって使用されますが、その他のファイルに含まれていないデータが格納されます。 ページング ファイルはすべてのプロセスによって使用され、ページング ファイル内の領域が不足している他のプロセスが実行中にエラーが発生します。|  
|**ピーク ページファイルのサイズ**|ページング ファイル内でこのプロセスが使用されるページの最大数。|  
|**ページ フォールト**|このプロセスで実行するスレッドによるページ フォールトの数。 ページ フォールトでは、スレッドがその作業をメイン メモリに設定されていない仮想メモリ ページを参照するときに発生します。 したがって、ページは取得されませんディスクからスタンバイ リスト上にある場合ため、メイン メモリ上に既にをもう 1 つ使用されているかどうか、またはのページを共有して処理します。|



