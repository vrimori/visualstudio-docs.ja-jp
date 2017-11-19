---
title: "グラフィックス フレームの検証 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.graphics.FrameValidation
ms.assetid: 1e639182-1301-4e28-9c1e-b5df732f3f1b
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9312ad8a96c5829aae21c87e78a0d5f2f0db1b35
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="graphics-frame-validation"></a>グラフィックス フレームの検証
<!-- VERSIONLESS -->
Visual Studio 2017 と大きいサポート、**フレーム検証**ツールです。  検証のフレーム ウィンドウには、エラーとイベントの一覧に関連付けられている警告が表示されます。  このウィンドウを表示するには、選択、**ビュー > フレーム検証**メニュー。

![フレームの検証](media/gfx_diag_frame_validation.png)

クリックして、**検証の実行**分析を開始する左上隅にあるボタンをクリックします。  フレームの複雑さによっては、完了するまでに数分かかる場合があります。  ここでは、2 つのソースからの組み合わせに表示されるデータ: メッセージを D3D 自体が出力時に[SDK レイヤー](https://msdn.microsoft.com/library/windows/desktop/ff476881(v=vs.85).aspx)が有効になってとツールの内部状態の追跡から収集されるデータ。 完了すると、複数のデータ列が表示されます。

**列**|**説明**
---|---
イベント ID | ID 内のエントリにマップされる、[イベント一覧](graphics-event-list.md)ウィンドウです。
重要度 | 破損、エラー、警告、情報、またはメッセージです。
カテゴリ | アプリケーションに定義され、その他、初期化、クリーンアップ、コンパイル、状態作成、状態の設定、状態を取得する、実行、リソースの操作、シェーダー、冗長なおよび未使用。
メッセージ | イベントに関連付けられているメッセージ。
イベント | エラーまたは警告に関連するイベントです。

## <a name="see-also"></a>関連項目  
[グラフィックス診断 (DirectX グラフィックスのデバッグ)](visual-studio-graphics-diagnostics.md)   
<!-- /VERSIONLESS -->