---
title: クラス タブ、ウィンドウのプロパティ ダイアログ ボックス |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Window Properties dialog box, Class Tab
ms.assetid: eaec9f07-d580-436d-934d-76c4e59439aa
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eaa02f87a0bb9737112121343226c2dc0e45937a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55015473"
---
# <a name="class-tab-window-properties-dialog-box"></a>[クラス] タブ ([ウィンドウ プロパティ] ダイアログ ボックス)
使用して、**クラス** タブを選択したウィンドウのクラスに情報を表示します。 表示する、[ウィンドウ プロパティ ダイアログ ボックス](../debugger/window-properties-dialog-box.md)、フォーカスを移動、 [Windows ビュー](../debugger/windows-view.md)ウィンドウ。 ツリーで、ウィンドウの任意のノードを選択し、**プロパティ**から、**ビュー**メニュー。  
  
 次の設定は [使用可能な**クラス**] タブ。  
  
|入力|説明|  
|-----------|-----------------|  
|**クラス名**|このウィンドウ クラスの名前 (または序数)。|  
|**クラス スタイル**|クラス スタイルのコードの組み合わせ。|  
|**クラス バイト数**|このウィンドウ クラスに関連付けられたアプリケーション固有のデータ。|  
|**クラス アトム**|によって返されるクラスを atom、 **RegisterClass**呼び出します。|  
|**インスタンス ハンドル**|クラスを登録したモジュールのインスタンス ハンドル。 インスタンス ハンドルが一意でないです。|  
|**ウィンドウ バイト数**|このクラスの各ウィンドウに関連付けられている追加のバイト数。 これらのバイトの意味は、アプリケーションによって決定されます。 DWORD 形式のバイト値を表示するリスト ボックスを展開します。|  
|**ウィンドウ プロシージャ**|現在のアドレス、 **WndProc**このクラスの windows の関数。 これに対し**ウィンドウ プロシージャ**上、**全般** タブ、ウィンドウをサブクラス化する場合。|  
|**メニュー名**|このクラス (メニューがない場合は「なし」) の windows に関連付けられているメイン メニューの名前。|  
|**アイコンハンドル**|このクラス (アイコンがない場合は「なし」) の windows に関連付けられているアイコンのハンドル。|  
|**カーソル ハンドル**|このクラス (カーソルがない場合は「なし」) の windows に関連付けられているカーソルのハンドル。|  
|**背景ブラシ**|このクラスは、または (ブラシがない場合は「なし」) ウィンドウの背景を描画する定義済みの色など * 色のいずれかの windows に関連付けられている背景ブラシのハンドル。|