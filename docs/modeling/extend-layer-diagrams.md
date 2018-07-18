---
title: 依存関係図を拡張します。
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, creating extensions
- layer models
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 304e1fe6356768ae5243ae38748d920444be41e9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31949281"
---
# <a name="extend-dependency-diagrams"></a>依存関係図を拡張します。
作成し、依存関係の図を更新し、Visual Studio での依存関係図と照らし合わせてプログラム コードの構造を検証するコードを記述することができます。 図のショートカット (コンテキスト) メニューに表示するコマンドを追加し、ドラッグ アンド ドロップ ジェスチャをカスタマイズし、テキスト テンプレートからレイヤー モデルにアクセスすることができます。 これらの拡張機能を VSIX (Visual Studio Integration Extension) にパッケージ化し、他の Visual Studio ユーザーに配布することができます。

 依存関係図についての詳細についてを参照してください。

-   [依存関係図: リファレンス](../modeling/layer-diagrams-reference.md)

-   [依存関係図: ガイドライン](../modeling/layer-diagrams-guidelines.md)

-   [コードからの依存関係図の作成](../modeling/create-layer-diagrams-from-your-code.md)

-   [依存関係図を使用したコードの検証](../modeling/validate-code-with-layer-diagrams.md)

##  <a name="prereqs"></a> 必要条件
 レイヤー拡張機能を開発するコンピューターに以下の項目がインストールされている必要があります。

-   Visual Studio

-   [Visual Studio SDK](../extensibility/visual-studio-sdk.md)

-   Visual Studio のモデリング SDK


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]


 適切なバージョンの Visual Studio をレイヤー拡張機能を実行するコンピューターにインストールしておく必要があります。 詳細については、次を参照してください。[レイヤー モデル拡張機能の配置](../modeling/deploy-a-layer-model-extension.md)です。

 Visual Studio のバージョンをサポートして、依存関係図を参照してください[アーキテクチャおよびモデリング ツールのバージョン サポート](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)です。

## <a name="in-this-section"></a>このセクションの内容
 [依存関係図にコマンドおよびジェスチャを追加する](../modeling/add-commands-and-gestures-to-layer-diagrams.md)

 [カスタム アーキテクチャ検証を依存関係図に追加する](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)

 [依存関係図へのカスタム プロパティの追加](../modeling/add-custom-properties-to-layer-diagrams.md)

 [プログラム コードでレイヤー モデル内を移動し、レイヤー モデルを更新する](../modeling/navigate-and-update-layer-models-in-program-code.md)

 [レイヤー モデル拡張機能の配置](../modeling/deploy-a-layer-model-extension.md)

 [依存関係図の拡張機能のトラブルシューティング](../modeling/troubleshoot-extensions-for-layer-diagrams.md)

## <a name="see-also"></a>関連項目

- [依存関係図: リファレンス](../modeling/layer-diagrams-reference.md)
- [依存関係図: ガイドライン](../modeling/layer-diagrams-guidelines.md)
- [コードからの依存関係図の作成](../modeling/create-layer-diagrams-from-your-code.md)
- [依存関係図を使用したコードの検証](../modeling/validate-code-with-layer-diagrams.md)
