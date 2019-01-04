---
title: SharePoint プロジェクト項目スキーマ リファレンス |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperty element
- SafeControls element
- SafeControl element
- .spdata files
- ExtensionData element
- FeatureProperties element
- ProjectOutputFile element
- Files element
- ProjectItemFolder element
- ProjectItemFile element
- ExtensionDataItem element
- ProjectItem element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e2023eb4828ab5ac59a45dd72040177a654176d7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53895806"
---
# <a name="sharepoint-project-item-schema-reference"></a>SharePoint プロジェクト項目スキーマのリファレンス
  Visual Studio の内容を検証する SharePoint プロジェクト項目のスキーマを使用して *.spdata*ファイル。 *.Spdata*ファイルは、SharePoint プロジェクト項目の動作とコンテンツを指定します。 SharePoint プロジェクト アイテムの内容に関する詳細については、次を参照してください。[項目テンプレートとの SharePoint プロジェクト アイテムのプロジェクト テンプレートを作成する](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)します。  
  
 SharePoint プロジェクト項目スキーマ ProjectItemModelSchema.xsd という名前が既定では、%program files (x86)%\Microsoft Visual Studio 11.0\Xml\Schemas インストールされています。  
  
 ルート要素は、 [ProjectItem](../sharepoint/projectitem-element.md)要素。 次の表では、すべてのスキーマによって定義される要素について説明します。  
  
|要素|説明|  
|-------------|-----------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|SharePoint プロジェクト アイテムに関連付けられているカスタム データ項目のコレクションを表します。|  
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|キー/値の形式で、SharePoint プロジェクト アイテムに関連付けられているカスタム データ項目を表します。 キーと値の両方には、文字列がある場合があります。|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|SharePoint に配置されるときに、機能に含まれているプロパティ値のコレクションを表します。 フィーチャーが配置されると、プロパティ値をコードでアクセスできます。|  
|[FeatureProperty](../sharepoint/featureproperty-element.md)|SharePoint に配置されるときに、機能に含まれているカスタム プロパティを表します。 フィーチャーが配置されると、コードでプロパティにアクセスすることができます。|  
|[ファイル](../sharepoint/files-element.md)|機能の要素ファイルまたはプロジェクトの出力など、SharePoint プロジェクト アイテムと共に配置するファイルを指定します。|  
|[ProjectItem](../sharepoint/projectitem-element.md)|SharePoint プロジェクト項目を表します。|  
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|機能の要素ファイルが SharePoint に展開するときに、プロジェクト項目に含めるなど、SharePoint のファイルを表します。|  
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|マップされたフォルダーを表します。|  
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|SharePoint に展開するときに、プロジェクト項目に含めるプロジェクトの出力を表します。|  
|[SafeControl](../sharepoint/safecontrol-element.md)|ASPX コントロールまたは SharePoint サイトのいずれかの ASPX ページにアクセスするすべてのユーザーに対してセキュリティで保護されたとして指定されている Web パーツを表します。|  
|[SafeControls](../sharepoint/safecontrols-element.md)|ASPX コントロールと、SharePoint サイト上のいずれかの ASPX ページにアクセスするすべてのユーザーに対してセキュリティで保護されたとして指定されている Web パーツのコレクションを表します。|  
  
## <a name="see-also"></a>関連項目
 [項目テンプレートとの SharePoint プロジェクト アイテムのプロジェクト テンプレートを作成します。](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)  
