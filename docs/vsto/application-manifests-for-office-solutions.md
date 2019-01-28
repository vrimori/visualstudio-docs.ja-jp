---
title: Office ソリューション用アプリケーション マニフェスト
ms.date: 02/02/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c9c15d7435fa6f5267e413e3afd0fd6e4c7ea17c
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54873705"
---
# <a name="application-manifests-for-office-solutions"></a>Office ソリューション用アプリケーション マニフェスト
  アプリケーション マニフェストは、Microsoft Office ソリューションに読み込まれるアセンブリについて記述した XML ファイルです。 Visual Studio での Office 開発ツールを使用して、[!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]アプリケーション マニフェスト スキーマで定義されている、 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)参照。

 Office ソリューション用のアプリケーション マニフェストは、次の [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 要素と属性を使用します。

|要素|説明|属性|
|-------------|-----------------|----------------|
|[&#60;アセンブリ&#62;要素&#40;ClickOnce アプリケーション&#41;](../deployment/assembly-element-clickonce-deployment.md)|必須。 最上位の要素です。|**manifestVersion**|
|[&#60;assemblyIdentity&#62;要素&#40;ClickOnce アプリケーション&#41;](../deployment/assemblyidentity-element-clickonce-deployment.md)|必須。 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] アプリケーションのプライマリ アセンブリを識別します。|**name**<br /><br /> **version**<br /><br /> **publicKeyToken**<br /><br /> **ProcessorArchitecture**<br /><br /> **language**|
|[&#60;trustInfo&#62;要素&#40;ClickOnce アプリケーション&#41;](../deployment/trustinfo-element-clickonce-application.md)|アプリケーションのセキュリティ要件を識別します。|なし|
|[&#60;entryPoint&#62;要素&#40;ClickOnce アプリケーション&#41;](../deployment/entrypoint-element-clickonce-application.md)|必須。 実行用のアプリケーション コードのエントリ ポイントを識別します。|**name**<br /><br /> **dependencyName**<br /><br /> **customHostSpecified**|
|[&#60;依存関係&#62;要素&#40;ClickOnce アプリケーション&#41;](../deployment/dependency-element-clickonce-deployment.md)|必須。 アプリケーションを実行するために必要な依存関係をそれぞれ識別します。 任意で、プレインストールする必要のあるアセンブリを識別します。|なし|
|[&#60;ファイル&#62;要素&#40;ClickOnce アプリケーション&#41;](../deployment/file-element-clickonce-application.md)|必須。 アプリケーションで使用する、アセンブリ以外の各ファイルを指定します。 ファイルに関連付けられているコンポーネント オブジェクト モデル (COM) 分離データを含めることができます。|**name**<br /><br /> **size**|

 Office ソリューション用アプリケーション マニフェストには、 `co.v1` 名前空間の次の要素があります。

```xml
<entryPoint>
    <co.v1:customHostSpecified />
</entryPoint>
```

 これらのアプリケーション マニフェストには、 `vstav3` 名前空間の次の要素と属性もあります。

```xml
<addIn>
  <entryPointsCollection>
    <entryPoints>
      <entryPoint>
      </entryPoint>
    </entryPoints>
  </entryPointsCollection>
  <update></update>
  <postActions>
    <postAction>
      <postActionData>
      </postActionData>
    <postAction>
  </postActions>
  <application>
    <customizations>
      <customization>
      </customization>
    </customizations>
  </application
</addIn>
```

|要素|説明|属性|
|-------------|-----------------|----------------|
|[&#60;customHostSpecified&#62;要素&#40;Visual Studio での Office 開発&#41;](../vsto/customhostspecified-element-office-development-in-visual-studio.md)|必須。 マニフェストを Office ソリューションとして明確にマークします。|なし|
|[&#60;addin&#62;要素&#40;Visual Studio での Office 開発&#41;](../vsto/addin-element-office-development-in-visual-studio.md)|必須。 エントリ ポイントを単一の名前空間に格納します。|なし|
|[&#60;entryPointsCollection&#62;要素&#40;Visual Studio での Office 開発&#41;](../vsto/entrypointscollection-element-office-development-in-visual-studio.md)|必須。 1 つ以上の Office ソリューション用のすべてのアセンブリをグループ化します。|**ID**|
|[&#60;entryPoints&#62;要素&#40;Visual Studio での Office 開発&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md)|必須。 Office ソリューションを実行するためのすべてのアセンブリをグループ化します。|なし|
|[&#60;entryPoint&#62;要素&#40;Visual Studio での Office 開発&#41;](../vsto/entrypoint-element-office-development-in-visual-studio.md)|必須。 Office ソリューションで実行するためのアセンブリを識別します。|**class**<br /><br /> **コントラクト**|
|[&#60;更新&#62;要素&#40;Visual Studio での Office 開発&#41;](../vsto/update-element-office-development-in-visual-studio.md)|必須。 ソリューションの更新を構成します。|**enabled**<br /><br /> **expiration**|
|[&#60;postActions&#62;要素&#40;Visual Studio での Office 開発&#41;](../vsto/postactions-element-office-development-in-visual-studio.md)|任意。 Office ソリューションのインストール後に実行される、すべての配置後アクションをグループ化します。|なし|
|[&#60;postAction&#62;要素&#40;Visual Studio での Office 開発&#41;](../vsto/postaction-element-office-development-in-visual-studio.md)|任意。 配置後アクションを識別します。|なし|
|[&#60;postActionData&#62;要素&#40;Visual Studio での Office 開発&#41;](../vsto/postactiondata-element-office-development-in-visual-studio.md)|任意。 配置後アクション用にデータを構成します。|なし|
|[&#60;アプリケーション&#62;要素&#40;Visual Studio での Office 開発&#41;](../vsto/application-element-office-development-in-visual-studio.md)|必須。 アプリケーション固有の情報を単一のノードにラップします。|なし|
|[&#60;カスタマイズ&#62;要素&#40;Visual Studio での Office 開発&#41;](../vsto/customizations-element-office-development-in-visual-studio.md)|必須。 アプリケーション ホスト固有のすべての情報を別個の名前空間に格納します。|なし|
|[&#60;カスタマイズ&#62;要素&#40;Visual Studio での Office 開発&#41;](../vsto/customization-element-office-development-in-visual-studio.md)|必須。 アプリケーション ホスト固有の情報を別個の名前空間に格納します。|**xmlns**|
|[&#60;ドキュメント&#62;要素&#40;Visual Studio での Office 開発&#41;](../vsto/document-element-office-development-in-visual-studio.md)|ドキュメント レベルのソリューションにのみ必須。 カスタマイズ固有の情報を格納します。|**solutionId**|
|[&#60;appAddin&#62;要素&#40;Visual Studio での Office 開発&#41;](../vsto/appaddin-element-office-development-in-visual-studio.md)|アプリケーション レベルのソリューションにのみ必須。 カスタマイズ固有の情報を格納します。|**application**<br /><br /> **LoadBehavior**<br /><br /> **keyName**|
|[&#60;friendlyName&#62;要素&#40;Visual Studio での Office 開発&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md)|任意。 インストールされている VSTO アドインの一覧に表示される VSTO アドインの名前を格納します。|なし|
|[&#60;説明&#62;要素&#40;Visual Studio での Office 開発&#41;](../vsto/description-element-office-development-in-visual-studio.md)|VSTO アドインにのみ必須。インストールされているプログラムの一覧に表示される説明を格納します。|なし|
|[&#60;formRegions&#62;要素&#40;Visual Studio での Office 開発&#41;](../vsto/formregions-element-office-development-in-visual-studio.md)|フォーム領域を含む Outlook VSTO アドインにのみ必須です。|なし|
|[&#60;formRegion&#62;要素&#40;Visual Studio での Office 開発&#41;](../vsto/formregion-element-office-development-in-visual-studio.md)|フォーム領域を含む Outlook VSTO アドインにのみ必須です。|**Name**|
|[&#60;vstoRuntime&#62;要素&#40;Visual Studio での Office 開発&#41;](../vsto/vstoruntime-element-office-development-in-visual-studio.md)|必須。 Office ソリューションでサポートされる、Visual Studio Tools for Office ランタイムの特定のバージョンを記述します。|**release**<br /><br /> **version**<br /><br /> **supportUrl**|

## <a name="remarks"></a>Remarks
 Office ソリューションのアプリケーション マニフェストと配置マニフェストは、手動で編集できます。 その後、アプリケーションを再署名する必要があり、配置が、マニフェストの生成および編集ツールを使用してマニフェスト (*mage.exe*と*mageui.exe*)。 詳細については、「[方法 :アプリケーション マニフェストと配置マニフェストの再署名](../deployment/how-to-re-sign-application-and-deployment-manifests.md)」を参照してください。

## <a name="file-location"></a>ファイルの場所
 アプリケーション マニフェストは単一のバージョンのソリューションに特有のものです。 このため、アプリケーション マニフェストは、配置マニフェストとは別の場所に格納する必要があります。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] は、バージョン固有のファイルを、発行フォルダーの *Application Files* サブディレクトリ内にある、関連するバージョンにちなんだ名前のサブディレクトリに格納します。

## <a name="file-name-syntax"></a>ファイル名の構文
 アプリケーションのマニフェスト ファイルの名前は、アプリケーションの拡張機能と完全な名前で識別される、 **assemblyIdentity**要素を拡張子が続きます *.manifest*します。 たとえば、参照するアプリケーション マニフェスト、 *OutlookAddIn1.dll*カスタマイズでは、次のファイル名構文を使用します。

 `OutlookAddIn1.dll.manifest`

## <a name="see-also"></a>関連項目

- [Office ソリューション用配置マニフェストします。](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)