---
title: "VSIX パッケージのローカライズ | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "パッケージをローカライズします。"
  - "拡張機能をローカライズします。"
  - "配置のローカライズ"
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# VSIX パッケージのローカライズ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ターゲット言語ごとに Extension.vsixlangpack ファイルを作成し、適切なフォルダーに配置して、VSIX パッケージをローカライズできます。 ローカライズされたパッケージがインストールされている場合は、ローカライズされた説明と共に、拡張機能のローカライズされた名前が表示されます。 ローカライズされたライセンス ファイル、またはローカライズされた情報を指す URL を指定すると、それらも表示されます。  
  
 かどうか、コンテンツ、VSIX パッケージには、VSPackage を追加するメニュー コマンドやその他の UI を参照してください。 [メニュー コマンドのローカライズ](../extensibility/localizing-menu-commands.md) については、新しい UI 要素をローカライズします。  
  
## ディレクトリ構造  
 ユーザーは、拡張機能をインストール **拡張機能と更新プログラム** 名前に一致する対象のコンピューターの Visual Studio ロケール フォルダー用の VSIX パッケージの最上位のレベルを確認します。 場合 **拡張機能と更新プログラム** .vsixlangpack 見つかるとファイルをフォルダー内、.vsixmanifest ファイルに対応する値をそのファイル内のローカライズされた値を代入しています。 拡張機能がインストールされるときに、これらの値が表示されます。 次の例では、スペイン語 \(es ES\) とフランス語 \(FR\) にローカライズされた VSIX パッケージのディレクトリ構造を示します。  
  
 MyExtension.dll  
  
 Extension.vsixmanifest  
  
 \[Content\_Types\] .xml  
  
 es\-ES  
  
 Extension.vsixlangpack  
  
 fr\-FR  
  
 Extension.vsixlangpack  
  
> [!NOTE]
>  VSIX でサポートされているプロジェクト テンプレート、 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] VSIX マニフェストを生成し、source.extension.vsixmanifest という名前を付けます。 Visual Studio によってプロジェクトがビルド時に、そのファイルの内容にコピー Extension.VsixManifest VSIX パッケージ内。  
  
## Extension.vsixlangpack ファイル  
 Extension.vsixlangpack ファイルは次の [VSIX 言語パック スキーマ](../extensibility/vsx-language-pack-schema-reference.md)します。 このスキーマには、 [VSIXLanguagePack](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md) ルート要素、およびこれらの 4 つの子要素: [LocalizedName](../extensibility/localizedname-element-vsix-language-pack-schema.md), 、[LocalizedDescription](../extensibility/localizeddescription-element-vsix-language-pack-schema.md), 、[詳細情報の Url](../extensibility/moreinfourl-element-vsix-language-pack-schema.md), 、および [ライセンス](../extensibility/license-element-vsix-language-pack-schema.md)します。 これらの子要素に対応して、 `Name`, 、`Description`, 、`MoreInfoURL`, 、および `License` の子要素、 `Identifier` Extension.vsixmanifest ファイルの要素。  
  
 設定する必要があります vsixlangpack ファイルを作成するときに、 `Include in Vsix` プロパティを `true`します。 それ以外の場合、ローカライズされたインストールのテキストは無視されます。  
  
#### Vsix プロパティで包含を設定するには  
  
1.  **ソリューション エクスプ ローラー**, 、Extension.vsixlangpack ファイルを右クリックし、 **プロパティ**します。  
  
2.  プロパティ グリッドで、クリックして **\[Vsix に含める**, 、その値に設定し、 `true`します。  
  
## 例  
  
### 説明  
 次の例では、スペイン語に対応する Extension.vsixlangpack ファイルと共に、Extension.vsixmanifest ファイルの関連部分を示します。 言語パックからの値は、対象のコンピューターの Visual Studio のロケールがスペイン語に設定されている場合、マニフェストから値を置き換えます。  
  
### コード  
 \[Extension.vsixmanifest\]  
  
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
  
 \[Extension.vsixlangpack\]  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<VsixLanguagePack Version="1.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema-lp/2010">  
  <LocalizedName>Arbol de Familia</LocalizedName>  
  <LocalizedDescription> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</LocalizedDescription>  
  <License>es\Eula.rtf</License>  
  <MoreInfoUrl> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfoUrl>  
</VsixLanguagePack>  
```  
  
## 参照  
 [VSIX LanguagePack 要素](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)   
 [VSIX パッケージの構造](../extensibility/anatomy-of-a-vsix-package.md)   
 [VSIX プロジェクト テンプレート](../extensibility/vsix-project-template.md)