---
title: グラフィックス フレームの検証 |Microsoft Docs
ms.date: 03/02/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.FrameValidation
ms.assetid: 1e639182-1301-4e28-9c1e-b5df732f3f1b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b353954f56cc71922d1ec5e7aef483c7bad2f47f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54991529"
---
# <a name="graphics-frame-validation"></a>グラフィックス フレームの検証
<!-- VERSIONLESS --> Visual Studio 2017 とサポートを強化、**フレームの検証**ツール。  フレームの検証のウィンドウには、エラーとイベントの一覧に関連付けられている警告が表示されます。  このウィンドウを表示するには、選択、**ビュー > フレームの検証**メニュー。

![フレームの検証](media/gfx_diag_frame_validation.png)

をクリックして、**検証の実行**分析を開始する左上隅にあるボタンをクリックします。  フレームの複雑さによっては完了までに数分かかる場合があります。  2 つのソースからの組み合わせは、ここに表示されるデータ: メッセージを D3D ときに出力自体[SDK レイヤー](/windows/desktop/direct3d11/overviews-direct3d-11-devices-layers)が有効になってと追跡ツールの内部状態から収集されるデータ。 完了すると、いくつかの列のデータが表示されます。


| **列** | **説明** |
|------------| - |
| イベント ID | ID 内のエントリにマップ、[イベント一覧](graphics-event-list.md)ウィンドウ。 |
| 重要度 | 破損、エラー、警告、情報、またはメッセージ。 |
| カテゴリ | アプリケーションに定義され、その他、初期化、クリーンアップ、コンパイル、状態作成、状態の設定、状態を取得する、実行、リソースの操作、シェーダー、冗長であり、使用されていません。 |
| メッセージ | イベントに関連付けられているメッセージ。 |
| event | エラーまたは警告に関連するイベントです。 |

## <a name="see-also"></a>「  
[グラフィックス診断 (DirectX グラフィックスのデバッグ)](visual-studio-graphics-diagnostics.md)   
<!-- /VERSIONLESS -->