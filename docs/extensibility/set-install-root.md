---
title: VSIX v3 と拡張機能フォルダー外にインストールする |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/09/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8476b300974d66efc60f647c897ec6892191e7fa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31136784"
---
# <a name="installing-outside-the-extensions-folder"></a>拡張機能フォルダー外にインストールします。

Visual Studio 2017 と VSIX v3 以降 (バージョン 3)、今すぐに対するサポートが拡張機能フォルダーの外部で資産を拡張機能をインストールします。 現時点では、次の場所は、([INSTALLDIR] は、Visual Studio のインスタンスのインストール ディレクトリにマッピング) の有効なインストール場所として有効になっているは。

* [INSTALLDIR] \MSBuild
* [INSTALLDIR] \Xml\Schemas
* [INSTALLDIR] \Common7\IDE\PublicAssemblies
* [INSTALLDIR] \Licenses
* [INSTALLDIR] \Common7\IDE\ReferenceAssemblies
* [INSTALLDIR] \Common7\IDE\RemoteDebugger
* [INSTALLDIR] \Common7\IDE\VC\VCTargets

>**注:** VSIX 形式、VS インストール フォルダー構造の外部のインストールはできません。

これらのディレクトリへのインストールをサポートするために VSIX を「インスタンスごとに、コンピューターごと」インストールする必要があります。 これは、extension.vsixmanifest の各デザイナーで"all users"チェック ボックスをオンに有効にすることができます。

![すべてのユーザーを確認します。](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>として「installroot」を設定する方法

インストール ディレクトリを設定するに使用することができます、**プロパティ**Visual Studio のウィンドウ。 たとえば、設定、`InstallRoot`上記の場所のいずれかへの参照をプロジェクトのプロパティ。

![ルートのプロパティをインストールします。](media/install-root-properties.png)

これには、対応にいくつかのメタデータが追加`ProjectReference`VSIX プロジェクトの .csproj ファイル内のプロパティ。

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

>**注:** したい場合、.csproj ファイルを直接、編集することができます。

## <a name="how-to-set-a-subpath-under-the-installroot"></a>として「installroot」下サブパスを設定する方法

下にサブ パスにインストールするかかどうか、 `InstallRoot`、できるように設定して、`VsixSubPath`プロパティと同じように、`InstallRoot`プロパティです。 たとえばにインストールする場合、プロジェクト参照の出力を選びました ' [INSTALLDIR]\MSBuild\MyCompany\MySDK\1.0' です。 そのために簡単にプロパティ デザイナーを使用。

![セットのサブパス](media/set-subpath.png)

.Csproj の対応する変更は、次のようになります。

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>追加情報

プロジェクト参照単にプロパティ デザイナー変更が適用します。設定することができます、`InstallRoot`も、プロジェクト内で項目のメタデータ (上記と同じ方法を使用)。
