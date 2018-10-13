---
title: VSIX パッケージのローカライズ |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 49ec131e4fa5ec635fa63763ccac9493134e2f2c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49292904"
---
# <a name="localizing-vsix-packages"></a>VSIX パッケージのローカライズ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSIX パッケージは、各ターゲット言語 Extension.vsixlangpack ファイルを作成し、適切なフォルダーに配置してローカライズできます。 ローカライズされたパッケージがインストールされている場合は、ローカライズされた説明と共に、拡張機能のローカライズされた名前が表示されます。 ローカライズされたライセンス ファイル、またはローカライズされた情報を指す URL を指定する場合は、それらも表示されます。  
  
 コンテンツ、VSIX パッケージに追加する VSPackage が含まれている場合メニュー コマンドやその他の UI を参照してください。[メニュー コマンドのローカライズ](../extensibility/localizing-menu-commands.md)については、新しい UI 要素をローカライズします。  
  
## <a name="directory-structure"></a>ディレクトリの構造  
 ユーザーは、拡張機能をインストール**拡張機能と更新**VSIX パッケージの名前を持つ対象のコンピューターの Visual Studio ロケールに一致するフォルダーの最上位のレベルを確認します。 場合**拡張機能と更新**.vsixlangpack を見つけるファイル、フォルダー、.vsixmanifest ファイル内の対応する値をそのファイルでローカライズされた値を代入しています。 拡張機能がインストールされるときに、これらの値が表示されます。 次の例では、スペイン語 (ES-ES) とフランス語 (FR) にローカライズされた VSIX パッケージのディレクトリ構造を示します。  
  
 MyExtension.dll  
  
 extension.vsixmanifest  
  
 [Content_Types] .xml  
  
 es-ES  
  
 Extension.vsixlangpack  
  
 fr-FR  
  
 Extension.vsixlangpack  
  
> [!NOTE]
>  VSIX でサポートされているプロジェクトのテンプレート、 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] VSIX マニフェストを生成し、source.extension.vsixmanifest という名前を付けます。 Visual Studio がプロジェクトをビルドするときにそのファイルの内容にコピー Extension.VsixManifest VSIX パッケージ内。  
  
## <a name="the-extensionvsixlangpack-file"></a>Extension.vsixlangpack ファイル  
 Extension.vsixlangpack ファイルは次の[VSIX 言語パックのスキーマ](../extensibility/vsx-language-pack-schema-reference.md)します。 このスキーマは、 [VSIXLanguagePack](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)ルート要素、およびこれらの 4 つの子要素: [LocalizedName](../extensibility/localizedname-element-vsix-language-pack-schema.md)、 [LocalizedDescription](../extensibility/localizeddescription-element-vsix-language-pack-schema.md)、 [MoreInfoURL](../extensibility/moreinfourl-element-vsix-language-pack-schema.md)、および[ライセンス](../extensibility/license-element-vsix-language-pack-schema.md)します。 これらの子要素に対応して、 `Name`、 `Description`、 `MoreInfoURL`、および`License`の子要素、 `Identifier` Extension.vsixmanifest ファイルの要素。  
  
 設定する必要があります vsixlangpack ファイルを作成するときに、`Include in Vsix`プロパティを`true`します。 それ以外の場合、ローカライズされたインストールのテキストは無視されます。  
  
#### <a name="to-set-the-include-in-vsix-property"></a>Vsix のプロパティで、含めるを設定するには  
  
1.  **ソリューション エクスプ ローラー**Extension.vsixlangpack ファイルを右クリックし、クリックして**プロパティ**します。  
  
2.  プロパティ グリッドで、クリックして**Vsix に含める**、その値に設定し、`true`します。  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 次の例では、スペイン語の場合、対応する Extension.vsixlangpack ファイルと共に、Extension.vsixmanifest ファイルの関連部分を示します。 言語パックからの値は、ターゲット コンピューターの Visual Studio のロケールがスペイン語に設定されている場合、マニフェストから値を置き換えます。  
  
### <a name="code"></a>コード  
 [Extension.vsixmanifest]  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<VSIX ...>  
  <Identifier ...>  
    <Name>Family Tree</Name>  
    <Description>This extension places a custom treeview control in the toolbox that is optimized for handling family tree information.</Description>  
    <License>EULA.rtf</License>  
    <MoreInfoURL>http://www.contoso.com/products/FamilyTree.htm</MoreInfoURL>  
    ...  
  </Identifier>  
  <References .../>  
  <Content .../>  
</VSIX>  
```  
  
 [Extension.vsixlangpack]  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<VsixLanguagePack Version="1.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema-lp/2010">  
  <LocalizedName>Arbol de Familia</LocalizedName>  
  <LocalizedDescription> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</LocalizedDescription>  
  <License>es\Eula.rtf</License>  
  <MoreInfoUrl> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfoUrl>  
</VsixLanguagePack>  
```  
  
## <a name="see-also"></a>関連項目  
 [VSIX LanguagePack 要素](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)   
 [VSIX パッケージの構造](../extensibility/anatomy-of-a-vsix-package.md)   
 [VSIX プロジェクト テンプレート](../extensibility/vsix-project-template.md)

