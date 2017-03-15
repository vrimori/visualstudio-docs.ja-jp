---
title: "VSIX v3 で拡張機能フォルダー外にインストールする |Microsoft ドキュメント"
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
translationtype: Machine Translation
ms.sourcegitcommit: 4e8ceb1c988f639d0ea18b94e206ddec2d3e764c
ms.openlocfilehash: 5c103b5f038260a17f64af56f78f0b3f37e3bb32
ms.lasthandoff: 02/22/2017

---
# <a name="installing-outside-the-extensions-folder"></a>拡張機能フォルダー外にインストールします。

>**注:**このドキュメントは暫定版であり、Visual Studio 2017 RC リリースに基づいています。

以降では、Visual Studio 2017 と VSIX v3 (バージョン 3)、機能拡張フォルダーの外部で資産を拡張機能をインストールするためここではサポートされています。 現時点では、次の場所は ([installdir] は、Visual Studio インスタンスのインストール ディレクトリにマッピング) の有効なインストール場所として有効にします。

* [installdir] \Common7\IDE\PublicAssemblies
* [installdir] \Common7\IDE\ReferenceAssemblies
* [installdir] \MSBuild
* [installdir] \Schemas
* [installdir] \Licenses
* [installdir] \RemoteDebugger
* [installdir] \VSTargets

>**注:** VSIX 形式 VS インストール フォルダーの構造体の外部のインストールはできません。

これらのディレクトリへのインストールをサポートするために、VSIX を「インスタンスごとのコンピューターごとの」インストールする必要があります。 これは、extension.vsixmanifest の各デザイナーで"all users"チェック ボックスをオンに有効にすることができます。

![すべてのユーザーを確認します。](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>として「installroot」を設定する方法

インストール ディレクトリを設定するには、使用することができます、**プロパティ**Visual Studio のウィンドウです。 たとえば、設定、`InstallRoot`上の場所のいずれかへの参照をプロジェクトのプロパティ。

![ルートのプロパティをインストールします。](media/install-root-properties.png)

これは、いくつかのメタデータが、対応する追加されます`ProjectReference`VSIX プロジェクトの .csproj ファイル内のプロパティ。

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

>**注:**したい場合、.csproj ファイルを直接、編集することができます。

## <a name="how-to-set-a-subpath-under-the-installroot"></a>として「installroot」下サブパスを設定する方法

下にあるサブパスをインストールするようにかどうか、 `InstallRoot`、できるように設定して、`VsixSubPath`プロパティと同様に、`InstallRoot`プロパティです。 たとえば、プロジェクト参照の出力をインストールしたい ' [installdir]\MSBuild\MyCompany\MySDK\1.0' です。 それが可能に簡単にプロパティ デザイナーを使用します。

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

プロパティのデザイナー変更はプロジェクト参照だけに適用します。設定することができます、`InstallRoot`も、プロジェクト内のアイテムのメタデータ (上記で説明したのと同じ方法を使用)。

