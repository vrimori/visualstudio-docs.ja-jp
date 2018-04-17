---
title: '方法: VSIX パッケージへの依存関係の追加 |Microsoft ドキュメント'
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
ms.openlocfilehash: 0704a72ba70e2a00baab99d327702ec6c08f1775
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>方法: VSIX パッケージへの依存関係の追加

ターゲット コンピューターに含まれていないすべての依存関係をインストールする VSIX パッケージの配置を設定することができます。 これを実現するには、source.extension.vsixmanifest ファイルを VSIX の依存関係が含まれます。

## <a name="to-add-a-dependency"></a>依存関係を追加するには

1. Source.extension.vsixmanifest ファイルを開き、**デザイン**ビュー。 移動して、**の依存関係** タブでをクリックし、**新規**です。

2. インストールした拡張機能を追加する: で、**新しい依存関係の追加**ダイアログ ボックスで、**拡張機能がインストールされている**し、**名前**一覧に拡張機能を選択します。

3. インストールされていない別の VSIX に追加する:: で、**新しい依存関係の追加**ダイアログ ボックスで、**ファイル システム上のファイル**しを使用して、**参照**VSIX を選択するボタンをクリックします。

## <a name="require-a-specific-visual-studio-release"></a>特定の Visual Studio リリースが必要

拡張機能は、Visual Studio 2017 の特定のバージョンを必要とする場合、15.3 でリリースされた機能に依存しているなどの VSIX にビルド番号を指定することができます**は InstallationTarget**です。 たとえば、15.3 のリリースでは、'15.0.26730.3' のビルド番号があります。 リリース ビルドの番号へのマッピングを確認できます[ここ](../install/visual-studio-build-numbers-and-release-dates.md)です。 リリース番号 '15.3' を使用して、正しく動作しないことに注意してください。

拡張機能 15.3 や以降では、宣言する場合、**は InstallationTarget バージョン**として [15.0.26730.3, 16.0)。

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```

VSIXInstaller では、Visual Studio の以前のバージョンを検出し、以降の更新プログラムが必要であるユーザーに通知します。


## <a name="see-also"></a>関連項目

 [VSIX 拡張機能スキーマ 1.0 リファレンス](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b) [VSIX パッケージの構造は](../extensibility/anatomy-of-a-vsix-package.md) [Windows インストーラーの配置の拡張機能の準備](../extensibility/preparing-extensions-for-windows-installer-deployment.md)