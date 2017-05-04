---
title: "Office ソリューション用アプリケーション マニフェスト | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "アプリケーション マニフェスト [Visual Studio での Office 開発]"
ms.assetid: dd38685f-f429-4a35-8c11-a03372c9770a
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# Office ソリューション用アプリケーション マニフェスト
  アプリケーション マニフェストは、Microsoft Office ソリューションに読み込まれるアセンブリについて記述した XML ファイルです。 Visual Studio の Microsoft Office 開発ツールでは、[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] アプリケーション マニフェスト スキーマを使用します。このスキーマは、「[ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)」リファレンスで定義されています。  
  
 Office ソリューション用のアプリケーション マニフェストは、次の [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 要素と属性を使用します。  
  
|要素|説明|属性|  
|--------|--------|--------|  
|[&#60;assembly&#62; 要素 &#40;ClickOnce アプリケーション&#41;](../Topic/%3Cassembly%3E%20Element%20(ClickOnce%20Application).md)|必須。 最上位の要素です。|`manifestVersion`|  
|[&#60;assemblyIdentity&#62; 要素 &#40;ClickOnce アプリケーション&#41;](../Topic/%3CassemblyIdentity%3E%20Element%20(ClickOnce%20Application).md)|必須です。[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] アプリケーションのプライマリ アセンブリを識別します。|`name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `language`|  
|[&#60;trustInfo&#62; 要素 &#40;ClickOnce アプリケーション&#41;](../Topic/%3CtrustInfo%3E%20Element%20(ClickOnce%20Application).md)|アプリケーションのセキュリティ要件を識別します。|なし|  
|[&#60;entryPoint&#62; 要素 &#40;ClickOnce アプリケーション&#41;](../Topic/%3CentryPoint%3E%20Element%20(ClickOnce%20Application).md)|必須です。 実行用のアプリケーション コードのエントリ ポイントを識別します。|`name`<br /><br /> `dependencyName`<br /><br /> `customHostSpecified`|  
|[&#60;dependency&#62; 要素 &#40;ClickOnce アプリケーション&#41;](../Topic/%3Cdependency%3E%20Element%20(ClickOnce%20Application).md)|必須です。 アプリケーションを実行するために必要な依存関係をそれぞれ識別します。 任意で、プレインストールする必要のあるアセンブリを識別します。|なし|  
|[&#60;file&#62; 要素 &#40;ClickOnce アプリケーション&#41;](../Topic/%3Cfile%3E%20Element%20(ClickOnce%20Application).md)|必須です。 アプリケーションで使用する、アセンブリ以外の各ファイルを指定します。 ファイルに関連付けられているコンポーネント オブジェクト モデル \(COM\) 分離データを含めることができます。|`name`<br /><br /> `size`|  
  
 Office ソリューション用アプリケーション マニフェストには、`co.v1` 名前空間の次の要素があります。  
  
```  
<entryPoint> <co.v1:customHostSpecified /> </entryPoint>   
```  
  
 これらのアプリケーション マニフェストには、`vstav3` 名前空間の次の要素と属性もあります。  
  
```  
<addIn> <entryPointsCollection> <entryPoints> <entryPoint> </entryPoint> </entryPoints> </entryPointsCollection> <update></update> <postActions> <postAction> <postActionData> </postActionData> <postAction> </postActions> <application> <customizations> <customization> </customization> </customizations> </application </addIn>  
```  
  
|要素|説明|属性|  
|--------|--------|--------|  
|[&#60;customHostSpecified&#62; 要素 &#40;Visual Studio での Office 開発&#41;](../vsto/customhostspecified-element-office-development-in-visual-studio.md)|必須です。 マニフェストを Office ソリューションとして明確にマークします。|なし|  
|[&#60;addin&#62; 要素 &#40;Visual Studio での Office 開発&#41;](../vsto/addin-element-office-development-in-visual-studio.md)|必須です。 エントリ ポイントを単一の名前空間に格納します。|なし|  
|[&#60;entryPointsCollection&#62; 要素 &#40;Visual Studio での Office 開発&#41;](../vsto/entrypointscollection-element-office-development-in-visual-studio.md)|必須です。 1 つ以上の Office ソリューション用のすべてのアセンブリをグループ化します。|`id`|  
|[&#60;entryPoints&#62; 要素 &#40;Visual Studio での Office 開発&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md)|必須です。 Office ソリューションを実行するためのすべてのアセンブリをグループ化します。|なし|  
|[&#60;entryPoint&#62; 要素 &#40;Visual Studio での Office 開発&#41;](../vsto/entrypoint-element-office-development-in-visual-studio.md)|必須です。 Office ソリューションで実行するためのアセンブリを識別します。|`class`<br /><br /> `contract`|  
|[&#60;update&#62; 要素 &#40;Visual Studio での Office 開発&#41;](../vsto/update-element-office-development-in-visual-studio.md)|必須です。 ソリューションの更新を構成します。|`enabled`<br /><br /> `expiration`|  
|[&#60;postActions&#62; 要素 &#40;Visual Studio での Office 開発&#41;](../vsto/postactions-element-office-development-in-visual-studio.md)|省略可能です。 Office ソリューションのインストール後に実行される、すべての配置後アクションをグループ化します。|なし|  
|[&#60;postAction&#62; 要素 &#40;Visual Studio での Office 開発&#41;](../vsto/postaction-element-office-development-in-visual-studio.md)|省略可能です。 配置後アクションを識別します。|なし|  
|[&#60;postActionData&#62; 要素 &#40;Visual Studio での Office 開発&#41;](../vsto/postactiondata-element-office-development-in-visual-studio.md)|省略可能です。 配置後アクション用にデータを構成します。|なし|  
|[&#60;application&#62; 要素 &#40;Visual Studio での Office 開発&#41;](../vsto/application-element-office-development-in-visual-studio.md)|必須です。 アプリケーション固有の情報を単一のノードにラップします。|なし|  
|[&#60;customizations&#62; 要素 &#40;Visual Studio での Office 開発&#41;](../vsto/customizations-element-office-development-in-visual-studio.md)|必須です。 アプリケーション ホスト固有のすべての情報を別個の名前空間に格納します。|なし|  
|[&#60;customization&#62; 要素 &#40;Visual Studio での Office 開発&#41;](../vsto/customization-element-office-development-in-visual-studio.md)|必須です。 アプリケーション ホスト固有の情報を別個の名前空間に格納します。|`xmlns`|  
|[&#60;document&#62; 要素 &#40;Visual Studio での Office 開発&#41;](../vsto/document-element-office-development-in-visual-studio.md)|ドキュメント レベルのソリューションにのみ必須。 カスタマイズ固有の情報を格納します。|`solutionId`|  
|[&#60;appAddin&#62; 要素 &#40;Visual Studio での Office 開発&#41;](../vsto/appaddin-element-office-development-in-visual-studio.md)|アプリケーション レベルのソリューションにのみ必須。 カスタマイズ固有の情報を格納します。|`application`<br /><br /> `loadBehavior`<br /><br /> `keyName`|  
|[&#60;friendlyName&#62; 要素 &#40;Visual Studio での Office 開発&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md)|省略可能です。 インストールされている VSTO アドインの一覧に表示される VSTO アドインの名前を格納します。|なし|  
|[&#60;description&#62; 要素 &#40;Visual Studio での Office 開発&#41;](../vsto/description-element-office-development-in-visual-studio.md)|VSTO アドインにのみ必須。 インストールされているプログラムの一覧に表示される説明を格納します。|なし|  
|[&#60;formRegions&#62; 要素 &#40;Visual Studio での Office 開発&#41;](../vsto/formregions-element-office-development-in-visual-studio.md)|フォーム領域を含む Outlook VSTO アドインにのみ必須です。|なし|  
|[&#60;formRegion&#62; 要素 &#40;Visual Studio での Office 開発&#41;](../vsto/formregion-element-office-development-in-visual-studio.md)|フォーム領域を含む Outlook VSTO アドインにのみ必須です。|`Name`|  
|[&#60;vstoRuntime&#62; 要素 &#40;Visual Studio での Office 開発&#41;](../vsto/vstoruntime-element-office-development-in-visual-studio.md)|必須です。 Office ソリューションでサポートされる、Visual Studio Tools for Office ランタイムの特定のバージョンを記述します。|`release`<br /><br /> `version`<br /><br /> `supportUrl`|  
  
## 解説  
 Office ソリューションのアプリケーション マニフェストと配置マニフェストは、手動で編集できます。 アプリケーション マニフェストと配置マニフェストを編集した後は、マニフェスト生成および編集ツール \(mage.exe および mageui.exe\) を使用して再署名する必要があります。 詳細については、「[方法: アプリケーション マニフェストおよび配置マニフェストに再署名する](../Topic/How%20to:%20Re-sign%20Application%20and%20Deployment%20Manifests.md)」を参照してください。  
  
## ファイルの場所  
 アプリケーション マニフェストは単一のバージョンのソリューションに特有のものです。 このため、アプリケーション マニフェストは、配置マニフェストとは別の場所に格納する必要があります。[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] は、バージョン固有のファイルを、発行フォルダーの **Application Files** サブディレクトリ内にある、関連するバージョンにちなんだ名前のサブディレクトリに格納します。  
  
## ファイル名の構文  
 アプリケーション マニフェスト ファイルの名前は、`assemblyIdentity` 要素に指定されたアプリケーションの完全名と拡張子に、.manifest という拡張子を付けたものにします。 たとえば、OutlookAddIn1.dll カスタマイズを参照するアプリケーション マニフェストは、次のようなファイル名構文を使用します。  
  
 `OutlookAddIn1.dll.manifest`  
  
## 参照  
 [Office ソリューション用配置マニフェスト](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)  
  
  