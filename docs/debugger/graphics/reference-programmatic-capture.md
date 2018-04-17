---
title: 参照 (プログラムによるキャプチャ) |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
ms.assetid: ef60eb8d-1ac2-4e3a-9b4b-f6da0bdd9da8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cf5a475c32fa1e9ecb3d376f7844ddbeeee7748c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="reference-programmatic-capture"></a>参照 (プログラムによるキャプチャ)
グラフィックス診断は、プログラム キャプチャ API によってキャプチャ機能のプログラムによる制御をサポートします。 この API を使用すると、メッセージをグラフィックス診断 HUD (ヘッドアップ ディスプレイ) に切り替えたり、追加したり、グラフィック ログ ファイルを初期化および作成したり、グラフィックス情報をキャプチャしたりできます。  
  
## <a name="programmatic-capture-apis"></a>プログラム キャプチャ API  
  
### <a name="classes"></a>クラス  
  
|名前|説明|  
|----------|-----------------|  
|[VsgDbg クラス](vsgdbg-class.md)|グラフィックス診断のアプリ内コンポーネントのプログラムによる制御に使用するインターフェイスを表します。|  
  
### <a name="preprocessor-symbols"></a>プリプロセッサ シンボル  
  
|名前|説明|  
|----------|-----------------|  
|[DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)|その存在によって、グラフィックス ログ ファイルがユーザーの一時ファイル ディレクトリに保存されるかどうかを定義します。|  
|[VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)|グラフィックス ログ ファイルの既定のファイル名を定義します。|  
|[VSG_NODEFAULT_INSTANCE](vsg-nodefault-instance.md)|その存在によって、`VsgDbg` クラスの既定のインスタンスが提供されるかどうかを定義します。|  
  
## <a name="related-articles"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[Capturing Graphics Information](capturing-graphics-information.md)|[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のグラフィックス診断ツールを使用してレンダリングに関する問題を診断できるように、DirectX ベースのアプリからグラフィックス情報をキャプチャする方法を示します。|  
|[概要](overview-of-visual-studio-graphics-diagnostics.md)|グラフィックス診断によって、DirectX ベースのゲームやアプリのレンダリング エラーのデバッグがどのように簡単になるかを示します。|