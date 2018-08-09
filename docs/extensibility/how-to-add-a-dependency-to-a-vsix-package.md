---
title: '方法: VSIX パッケージへの依存関係の追加 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 54b4bf86df74a60dbeabef5c6f375354c5a945aa
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/08/2018
ms.locfileid: "39636689"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>方法: VSIX パッケージへの依存関係の追加

ターゲット コンピューターに含まれていないすべての依存関係をインストールする VSIX パッケージの配置を設定することができます。 これを行うには、VSIX の依存関係を*source.extension.vsixmanifest*ファイル。

## <a name="to-add-a-dependency"></a>依存関係を追加するには

1. 開く、 *source.extension.vsixmanifest*ファイル、**デザイン**ビュー。 移動して、**依存関係** タブでをクリックし、**新規**します。

2. インストールされている拡張機能を追加する: で、**新しい依存関係の追加**ダイアログ ボックスで、**拡張機能がインストールされている**し、**名前**リストの拡張機能を選択します。

3. インストールされていない別の VSIX を追加する: で、**新しい依存関係の追加**ダイアログ ボックスで、**ファイル システム上のファイル**しを使用して、**参照**VSIX を選択するボタンをクリックします。

## <a name="require-a-specific-visual-studio-release"></a>特定の Visual Studio リリースが必要です。

拡張機能には、特定のバージョンの Visual Studio 2017 が必要とする場合など 15.3 でリリースされた機能に依存、ビルド番号を指定するには、VSIX の**InstallationTarget**します。 たとえば、15.3 のリリースでは、'15.0.26730.3' のビルド番号があります。 ビルド番号のリリースのマッピングを確認できます[ここ](../install/visual-studio-build-numbers-and-release-dates.md)します。 なお、リリースを使用して数 '15.3' が正しく動作しません。

拡張機能が 15.3 が必要ですか、以降では、宣言する場合、 **InstallationTarget バージョン**として [15.0.26730.3, 16.0)。

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```

VSIXInstaller は Visual Studio の以前のバージョンを検出し、以降の更新プログラムが必要であるユーザーに通知します。


## <a name="see-also"></a>関連項目

 [VSIX 拡張機能スキーマ 1.0 リファレンス](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [VSIX パッケージの構造](../extensibility/anatomy-of-a-vsix-package.md)   
 [Windows インストーラーの配置の拡張機能を準備します。](../extensibility/preparing-extensions-for-windows-installer-deployment.md)
