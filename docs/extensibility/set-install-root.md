---
title: "VSIX v3 と拡張機能フォルダー外にインストールする |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
caps.latest.revision: 1
author: gregvanl
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: da7f91cc71eb6d0bc403089a0e34b6d81165e026
ms.contentlocale: ja-jp
ms.lasthandoff: 09/06/2017

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

>**注:**したい場合、.csproj ファイルを直接、編集することができます。

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

