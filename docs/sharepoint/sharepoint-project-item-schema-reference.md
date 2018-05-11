---
title: SharePoint プロジェクト項目のスキーマ リファレンス |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
ms.openlocfilehash: 9b039b1cf31a04a24819b03114c661a3ab1b108a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sharepoint-project-item-schema-reference"></a>SharePoint プロジェクト項目スキーマのリファレンス
  Visual Studio では、SharePoint プロジェクト項目のスキーマを使用して、.spdata ファイルの内容を検証します。 .Spdata ファイルは、SharePoint プロジェクト項目の動作と内容を指定します。 SharePoint プロジェクト項目の内容に関する詳細については、次を参照してください。[項目テンプレートを作成し、SharePoint プロジェクト項目用のプロジェクト テンプレート](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)です。  
  
 SharePoint プロジェクト項目のスキーマは ProjectItemModelSchema.xsd という % プログラム ファイル (x86)%\Microsoft Visual Studio 11.0\Xml\Schemas 既定でインストールされます。  
  
 ルート要素が、 [ProjectItem](../sharepoint/projectitem-element.md)要素。 次の表では、すべてのスキーマで定義されている要素について説明します。  
  
|要素|説明|  
|-------------|-----------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|SharePoint プロジェクト アイテムに関連付けられているカスタム データ項目のコレクションを表します。|  
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|キー/値の形式で、SharePoint プロジェクト項目に関連付けられているカスタム データ項目を表します。 キーと値の両方には、文字列がある場合があります。|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|SharePoint に配置されるときに、機能に含まれているプロパティ値のコレクションを表します。 フィーチャーが配置されると、プロパティの値をコードでアクセスできます。|  
|[FeatureProperty](../sharepoint/featureproperty-element.md)|SharePoint に配置されるときに、機能に含まれているカスタム プロパティを表します。 フィーチャーが配置されると、コードでプロパティにアクセスすることができます。|  
|[ファイル](../sharepoint/files-element.md)|フィーチャー要素ファイルまたはプロジェクトの出力など、SharePoint プロジェクト項目と共に配置するファイルを指定します。|  
|[ProjectItem](../sharepoint/projectitem-element.md)|SharePoint プロジェクト項目を表します。|  
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|フィーチャー要素ファイルが SharePoint に展開するときに、プロジェクト項目に含めるなどの SharePoint ファイルを表します。|  
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|マップされたフォルダーを表します。|  
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|SharePoint に配置されるときに、プロジェクト項目に含めるプロジェクトの出力を表します。|  
|[SafeControl](../sharepoint/safecontrol-element.md)|ASPX コントロールまたは SharePoint サイト上の任意の ASPX ページにアクセスするすべてのユーザーのセキュリティで保護されたとして指定されている Web パーツを表します。|  
|[SafeControls](../sharepoint/safecontrols-element.md)|ASPX コントロールと、SharePoint サイト上の任意の ASPX ページにアクセスするすべてのユーザーのセキュリティで保護されたとして指定されている Web パーツのコレクションを表します。|  
  
## <a name="see-also"></a>関連項目  
 [SharePoint プロジェクト項目の項目テンプレートとプロジェクト テンプレートの作成](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)  
  
  