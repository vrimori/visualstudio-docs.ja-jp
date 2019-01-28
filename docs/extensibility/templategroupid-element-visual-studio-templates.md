---
title: TemplateGroupID 要素 (Visual Studio テンプレート) |Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateGroupID
helpviewer_keywords:
- TemplateGroupID element [Visual Studio Templates]
- <TemplateGroupID> element [Visual Studio Templates]
ms.assetid: bce7b49a-90bc-4691-aff3-a87e209f6d83
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: be9a74c4aedf49b9ff7f7d56c29f3281c2d4578f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54952809"
---
# <a name="templategroupid-element-visual-studio-templates"></a>TemplateGroupID 要素 (Visual Studio テンプレート)
項目テンプレートを表示するプロジェクトの種類を指定します。 この要素は、重要な場合に[ShowByDefault (Visual Studio テンプレート)](../extensibility/showbydefault-visual-studio-templates.md)に設定されている`false`します。 ときに[ShowByDefault (Visual Studio テンプレート)](../extensibility/showbydefault-visual-studio-templates.md)に設定されている`true`、項目テンプレートはすべてのプロジェクト タイプで使用できます。  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<TemplateGroupID>  
  
## <a name="syntax"></a>構文  
  
```  
<TemplateGroupID> ... </TemplateGroupID>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|テンプレートをカテゴリに分類し、 **[新しいプロジェクト]** ダイアログ ボックス、または **[新しい項目の追加]** ダイアログ ボックスでどのように表示させるかを定義します。|  
  
## <a name="text-value"></a>テキスト値  
 テキスト値が必要です。  
  
 このテキストは、項目テンプレートのカテゴリの識別子を指定します。  
  
## <a name="remarks"></a>Remarks  
 `TemplateGroupID` は要素です。  
  
 値、`TemplateGroupID`要素は、プロジェクト システムの登録と使用 (hkey_local_machine \software\microsoft\visualstudio\\*\<バージョン番号 >* \Projects\\)フィルター テンプレートに表示される、**新しい項目の追加** ダイアログ ボックス。  
  
|Visual C++ の値|説明|  
|------------------------|-------------|  
|VC-Native|ネイティブ プロジェクトに使用されます。 プロジェクトの種類を特定できない場合は、これが既定値になります。|  
|VC-Managed|マネージド (/clr) プロジェクトに使用されます|  
|VC-Windows|Windows プラットフォーム (ネイティブ/マネージ/ストア) を対象とするすべてのプロジェクトに使用されます|  
|WinRT-Native-UAP|Windows 10 ストア プロジェクトに使用されます|  
|CodeSharing-Native|共有済みの項目のプロジェクトに使用されます|  
|WinRT-Native-6.3|Windows 8.1 ストア プロジェクトに使用されます|  
|WinRT-Native-Phone-6.3|Windows Phone 8.1 プロジェクトに使用されます|  
|WinRT - ネイティブ|Windows 8.0 ストア プロジェクトに使用されます|  
|VC-Android|Android プロジェクトに使用されます|  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)   
 [プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)