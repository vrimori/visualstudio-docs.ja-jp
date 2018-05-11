---
ms.topic: include
ms.openlocfilehash: 78de57178350d4317896c41a455efbeeb553c58d
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
## <a name="install-the-connected-environment-cli"></a>Connected Environment CLI をインストールする
Connected Environment には、最小限のローカル コンピューターのセットアップが必要です。 開発環境のほとんどの構成はクラウドに格納され、他のユーザーと共有することができます。

### <a name="install-on-mac"></a>Mac にインストールする
Connected Environment CLI をダウンロードし、インストールする:
```cmd
curl -L https://aka.ms/get-vsce-mac | bash
```

### <a name="install-on-windows"></a>Windows にインストールする
1. [Connected Environment CLI インストーラー](https://aka.ms/get-vsce-windows)をダウンロードして、実行します。 

### <a name="install-on-linux"></a>Linux にインストールする
近日公開予定...

## <a name="get-kubernetes-debugging-for-vs-code"></a>VS Code 用の Kubernetes デバッグ ツールを入手する
Connected Environment CLI をスタンドアロン ツールとして使用できますが、VS Code を使用している .NET Core または Node.js 開発者であれば、Kubernetes デバッグなどの豊富な機能を使用できます。

1. お持ちでない場合、[VS Code](https://code.visualstudio.com/Download) をインストールしてください。
1. [VS Connected Environment 拡張機能](https://aka.ms/get-vsce-code)をダウンロードします。
1. 拡張機能をインストールする: 

```cmd
code --install-extension path-to-downloaded-extension/vsce-0.1.1.vsix
```
