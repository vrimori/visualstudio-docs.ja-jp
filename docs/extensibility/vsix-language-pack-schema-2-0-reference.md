---
title: "VSIX Language Pack 2.0 スキーマ参照 |Microsoft ドキュメント"
ms.custom: 
ms.date: 10/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language pack
- localize vsix
- localize package
- localize extension
ms.assetid: 2a2932bc-cdbe-4d32-91fa-a3e0474f9098
caps.latest.revision: "8"
ms.author: dagriffe
author: dgriffen
manager: ghogen
ms.workload: dagriffe
ms.openlocfilehash: b601653e4b2d309d41f32ff71666567ab860e698
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="vsix-language-pack-schema-20-reference"></a>VSIX Language Pack 2.0 スキーマ参照

VSIX Language Pack スキーマでは、VSIX パッケージのローカライズされたインストール情報を提供します。 このスキーマのバージョン 2.0 では、追加のローカリゼーション要素をサポートします。

## <a name="language-pack-schema"></a>言語パック スキーマ

言語パック ファイルのルート要素が`<PackageLanguagePackManifest>`の属性を持つ`Version`、言語パックの形式のバージョンであります。 このトピックの説明を設定して、マニフェストで指定されている言語パックの形式のバージョン 2.0、`Version`属性値を`Version="2.0.0"`です。 ルート要素には、正確に 1 つの子が含まれています。`<Metadata>`要素。

### <a name="packagelangaugepackmanifest-element"></a>PackageLangaugePackManifest 要素

内で、`<PackageLanguagePackManifest>`要素の次の要素が存在する必要があります。
|タイトル|説明|
|-----------|-----------------|
|`<Metadata>`| すべてのパッケージのローカライズされたメタデータを含む要素

### <a name="metadata-element"></a>メタデータ要素

内で、`<Metadata>`要素の次の要素を持つことができます。
|タイトル|説明|
|-----------|-----------------|
|`<DisplayName>`|インストールする拡張機能のローカライズされた名前|
|`<Description>`|インストールする拡張機能のローカライズされた説明|
|`<License>`| 拡張機能のライセンスのローカライズされたバージョンへのパス|
|`<MoreInfo>`| ローカライズされた拡張に関する情報へのリンク|
|`<ReleaseNotes>`| パスまたはリリース ノートのローカライズされたバージョンへのリンク|
|`<Icon>`| 拡張機能 アイコンのローカライズされたバージョンへのパス|

### <a name="sample-manifest"></a>サンプルのマニフェスト

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageLanguagePackManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <DisplayName>Arbol de Familia</LocalizedName>
    <Description> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</Description>
    <MoreInfo> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
</PackageLanguagePackManifest>
```

## <a name="see-also"></a>参照

|タイトル|説明|
|-----------|-----------------|
|[VSIX パッケージのローカライズ](../extensibility/localizing-vsix-packages.md)|VSIX パッケージのローカライズされたインストールのサポートを提供する方法を示します。|
|[VSIX 拡張機能スキーマ 2.0 リファレンス](../extensibility/vsix-extension-schema-2-0-reference.md)|VSIX マニフェストが Visual Studio の拡張を使用してインストールすることができます、.vsix 展開ファイルの内容を記述、**拡張機能と更新プログラム** ダイアログ ボックス。|
|[Visual Studio 拡張機能の検索と使用](../ide/finding-and-using-visual-studio-extensions.md)|使用する方法を示します、**拡張機能と更新**をインストール、削除、アクティブ化、および拡張機能を非アクティブ化 ダイアログ ボックス。|