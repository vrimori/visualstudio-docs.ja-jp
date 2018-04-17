---
title: ページファイル タブの プロセス プロパティ ダイアログ ボックス |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: daf41a06-8a55-48f6-95f5-49a8416bd308
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1c5a0b5b498eacab4f53471530f51f8c59aed25e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="page-file-tab-process-properties-dialog-box"></a>[ページ ファイル] タブ ([プロセス プロパティ] ダイアログ ボックス)
使用して、**ページファイル**タブは、プロセスのページング ファイルを確認します。 表示する、[プロセス プロパティ ダイアログ ボックス](../debugger/process-properties-dialog-box.md)にフォーカスを移動する、[プロセス ビュー](../debugger/processes-view.md)ウィンドウです。 ツリーで、プロセスの任意のノードを選択し、**プロパティ**から、**ビュー**メニュー。  
  
 次の設定が [利用可能な**ページファイル**] タブ。  
  
|入力|説明|  
|-----------|-----------------|  
|**ページファイルのサイズ**|ページング ファイル内でこのプロセスを使用しているページの現在数。 ページング ファイルは、プロセスによって使用されますが、その他のファイルに含まれていないデータのページを格納します。 すべてのプロセスによって、ページング ファイルが使用され、ページング ファイル内の領域が不足している他のプロセスの実行中にエラーが発生します。|  
|**ピーク ページファイルのサイズ**|ページング ファイル内でこのプロセスが使用されるページの最大数。|  
|**ページ フォールト**|このプロセスで実行するスレッドによるページ フォールトの数。 スレッドのワーキング セット メイン メモリに含まれていない仮想メモリのページを参照する場合、ページ フォールトが発生します。 したがって、ページは取得されませんディスクからスタンバイ リスト上にある場合と同じようメイン メモリ内の既存の間で使用されているかどうか、またはページを共有して処理します。|