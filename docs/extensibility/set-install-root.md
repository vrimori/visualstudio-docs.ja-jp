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
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: 6d87c86d0a7793f661c6a3b28e95340f3a28c616
ms.lasthandoff: 03/07/2017

---
# <a name="installing-outside-the-extensions-folder"></a>拡張機能フォルダー外にインストールします。

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

![すべてのユーザーを確認します。](~/docs/extensibility/media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>として「installroot」を設定する方法

インストール ディレクトリを設定するには、使用することができます、**プロパティ**Visual Studio のウィンドウです。 たとえば、設定、`InstallRoot`上の場所のいずれかへの参照をプロジェクトのプロパティ。

![ルートのプロパティをインストールします。](~/docs/extensibility/media/install-root-properties.png)

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

![セットのサブパス](~/docs/extensibility/media/set-subpath.png)

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

