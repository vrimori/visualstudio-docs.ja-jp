---
ms.topic: include
ms.openlocfilehash: dbf7482acb02c6347c9c0d0765ef962cfb43a050
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
## <a name="initialize-debug-assets-with-the-vs-code-extension"></a>VS Code 拡張機能でデバッグ アセットを初期化する
Azure で VS Code が開発環境と通信できるように、最初にコード プロジェクトを構成する必要があります。 Connected Environment の VS Code 拡張機能には、デバッグ構成を設定するためのヘルパー コマンドがあります。 

**[コマンド パレット]** を開き (**[表示] の [コマンド パレット]** メニューを使用します)、入力候補機能を利用して入力し、コマンド `Connected Environment: Create configuration files for connected development` を選択します。 

`.vscode` フォルダーの下に Connected Environment のデバッグ構成が追加されます。

![](../media/vsce-command-palette.png)

> [!Note]
> **重要**: 続行前に VS Code を一度閉じ、再度開いてください (これはバグに起因する措置です)。