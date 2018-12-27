---
title: VSIX パッケージのローカライズ |Microsoft Docs
ms.custom: ''
ms.date: 10/26/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 85d32f25e8dd1f2f56af0857f2be0ff24c4d3126
ms.sourcegitcommit: 159ed9d4f56cdc1dff2fd19d9dffafe77e46cd4e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2018
ms.locfileid: "53740248"
---
# <a name="localizing-vsix-packages"></a>VSIX パッケージのローカライズ

作成して VSIX パッケージをローカライズすることができます、 *Extension.vsixlangpack*ターゲット言語ごとにファイルを開き、適切なフォルダーに配置します。 ローカライズされたパッケージがインストールされている場合は、ローカライズされた説明と共に、拡張機能のローカライズされた名前が表示されます。 ローカライズされたライセンス ファイル、またはローカライズされた情報を指す URL を指定する場合は、それらも表示されます。

VSIX パッケージのコンテンツは追加する VSPackage が含まれる場合メニュー コマンドやその他の UI を参照してください。[メニュー コマンドのローカライズ](../extensibility/localizing-menu-commands.md)新しい UI 要素をローカライズする方法についてはします。

## <a name="directory-structure"></a>ディレクトリの構造

 ユーザーは、拡張機能をインストール**拡張機能と更新**VSIX パッケージの名前を持つ対象のコンピューターの Visual Studio ロケールに一致するフォルダーの最上位のレベルを確認します。 場合**拡張機能と更新**検索、 *.vsixlangpack*ファイル、フォルダー内の対応する値には、そのファイルでローカライズされた値を置き換える、 *.vsixmanifest*ファイル。 拡張機能がインストールされるときに、これらの値が表示されます。 次の例では、スペイン語 (ES-ES) とフランス語 (FR) にローカライズされた VSIX パッケージのディレクトリ構造を示します。  

```text
.
├── MyExtension.dll
├── Extension.vsixmanifest
├── [Content_Types].xml
├── es-ES
│   └── Extension.vsixlangpack
└── fr-FR
    └── Extension.vsixlangpack
```

> [!NOTE]
> VSIX でサポートされているプロジェクトのテンプレート、 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] VSIX マニフェストを生成し、名前を*source.extension.vsixmanifest*します。 Visual Studio がプロジェクトをビルドするときにそのファイルの内容にコピー Extension.VsixManifest VSIX パッケージ内。

## <a name="the-extensionvsixlangpack-file"></a>Extension.vsixlangpack ファイル

*Extension.vsixlangpack*ファイルの次のように、 [VSIX 言語パック スキーマ 2.0](../extensibility/vsix-language-pack-schema-2-0-reference.md)します。 このスキーマは、 `PackageLanguagePackManifest`、直後にこれを`Metadata`子要素。 メタデータ要素は、最大 6 の子要素を含めることができます`DisplayName`、 `Description`、 `MoreInfo`、 `License`、 `ReleaseNotes`、および`Icon`します。 これらの子要素に対応して、 `DisplayName`、 `Description`、 `MoreInfo`、 `License`、 `ReleaseNotes`、および`Icon`の子要素、`Metadata`の要素、 *Extension.vsixmanifest*ファイル。

設定する必要があります vsixlangpack ファイルを作成するときに、`Include in Vsix`プロパティを`true`します。 それ以外の場合、ローカライズされたインストールのテキストは無視されます。

### <a name="to-set-the-include-in-vsix-property"></a>Vsix のプロパティで、含めるを設定するには

1. **ソリューション エクスプ ローラー**Extension.vsixlangpack ファイルを右クリックし、クリックして**プロパティ**します。

2.  **プロパティ グリッド**、 をクリックして**Vsix に含める**、その値に設定し、`true`します。

## <a name="example"></a>例

### <a name="description"></a>説明

次の例では、関連する部分の*Extension.vsixmanifest*ファイル。 ファイルも含まれます、対応する*Extension.vsixlangpack*スペイン語用のファイル。 言語パックからの値は、ターゲット コンピューターの Visual Studio のロケールがスペイン語に設定されている場合、マニフェストから値を置き換えます。

### <a name="code"></a>コード

 [*Extension.vsixmanifest*]

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageManifest ...>
  <Metadata ...>
    <DisplayName>Family Tree</DisplayName>
    <Description>This extension places a custom treeview control in the toolbox that is optimized for handling family tree information.</Description>
    <MoreInfo>http://www.contoso.com/products/FamilyTree.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
  <Installation .../>
  <Dependencies .../>
  <Prerequisites .../>
  <Assets .../>
</PackageManifest>
```

 [*Extension.vsixlangpack*]

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageLanguagePackManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <DisplayName>Arbol de Familia</DisplayName>
    <Description> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</Description>
    <MoreInfo> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
</PackageLanguagePackManifest>
```

## <a name="see-also"></a>関連項目

|タイトル|説明|
|-----------|-----------------|
|[VSIX 言語パック スキーマ 2.0 リファレンス](/visualstudio/extensibility/vsix-language-pack-schema-2-0-reference)|VSIX 言語パックでは、.vsix 展開ファイルのローカリゼーションの情報について説明します。|
|[VSIX パッケージの構造](../extensibility/anatomy-of-a-vsix-package.md)|構造と vsix パッケージの内容について説明します。|
|[メニュー コマンドをローカライズします。](../extensibility/localizing-menu-commands.md)|拡張機能では、その他のテキスト リソースをローカライズする方法を示します。|