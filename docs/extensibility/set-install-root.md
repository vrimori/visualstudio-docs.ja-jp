---
title: VSIX v3 で拡張機能フォルダー外でのインストール |Microsoft Docs
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fc8d0ccac452d82ed1a2f5fbce7c88fd82efc1d7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54983106"
---
# <a name="installing-outside-the-extensions-folder"></a>拡張機能フォルダー外でのインストール

Visual Studio 2017 と VSIX v3 以降 (バージョン 3)、拡張機能フォルダーの外部で資産を拡張機能をインストールするためのサポートを開始しました。 現時点では、次の場所は、([INSTALLDIR] は、Visual Studio インスタンスのインストール ディレクトリにマップ) の有効なインストール場所として有効になっているは。

* [INSTALLDIR]\MSBuild
* [INSTALLDIR]\Xml\Schemas
* [INSTALLDIR]\Common7\IDE\PublicAssemblies
* [INSTALLDIR]\Licenses
* [INSTALLDIR]\Common7\IDE\ReferenceAssemblies
* [INSTALLDIR]\Common7\IDE\RemoteDebugger
* [INSTALLDIR]\Common7\IDE\VC\VCTargets

>**注:** VSIX 形式では、VS のインストール フォルダーの構造の外にインストールできません。

これらのディレクトリへのインストールをサポートするために、VSIX を「インスタンスごとのコンピューターごとの」インストールする必要があります。 これは、extension.vsixmanifest デザイナーで「すべてのユーザー」のチェック ボックスをオンに有効にすることができます。

![すべてのユーザーを確認してください。](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>InstallRoot を設定する方法

インストール ディレクトリを設定するには、使用することができます、**プロパティ**Visual Studio のウィンドウ。 たとえば、設定、`InstallRoot`上の場所のいずれかへの参照をプロジェクトのプロパティ。

![ルートのプロパティをインストールします。](media/install-root-properties.png)

これは、いくつかのメタデータが、対応する追加されます`ProjectReference`VSIX プロジェクトの .csproj ファイル内のプロパティ。

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

>**注:** たい場合は、.csproj ファイルを直接編集できます。

## <a name="how-to-set-a-subpath-under-the-installroot"></a>InstallRoot、下のサブパスを設定する方法

下のサブパスをインストールするかかどうか、 `InstallRoot`、設定によって行うことができます、`VsixSubPath`プロパティと同様、`InstallRoot`プロパティ。 たとえばをインストールする、プロジェクト参照の出力する ' [INSTALLDIR]\MSBuild\MyCompany\MySDK\1.0'。 次のように簡単にプロパティ デザイナーを使用しました。

![セットのサブパス](media/set-subpath.png)

対応する .csproj 変更は、次のようになります。

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>追加情報

プロパティのデザイナーの変更; プロジェクトの参照だけに適用されます。設定することができます、`InstallRoot`もプロジェクト内の項目のメタデータ (上記で説明したのと同じ方法を使用)。
