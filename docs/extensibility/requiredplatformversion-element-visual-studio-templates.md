---
title: "RequiredPlatformVersion 要素 (Visual Studio テンプレート) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 818405e6c7df6466208db325a7417e0b5b9387e2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="requiredplatformversion-element-visual-studio-templates"></a>RequiredPlatformVersion 要素 (Visual Studio テンプレート)
プロジェクト テンプレートが正しく動作するために必要なオペレーティング システムの最小バージョンを指定します。 この要素は [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] アプリを作成するプロジェクト テンプレートに使用されます。  
  
 `RequiredPlatformVersion` の値は、オペレーティング システムのバージョンと直接比較されます。 場合、`RequiredPlatformVersion`オペレーティング システムのバージョンよりも高い、テンプレートがない、**新しいプロジェクト** ダイアログ ボックス。 [!INCLUDE[win8](../debugger/includes/win8_md.md)] 以上のテンプレートを指定するには、`RequiredPlatformVersion` を 6.2.0 に設定します。 [!INCLUDE[win81](../debugger/includes/win81_md.md)] 以上のテンプレートを指定するには、RequiredPlatformVersion を 6.3.0 に設定します。  
  
 `RequiredPlatformVersion`=8 を指定できるテンプレートは、顧客の以前の [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] テンプレートと互換性があります。  
  
 VSTemplate  
TemplateData  
.....TargetPlatformName  
RequiredPlatformVersion  
  
## <a name="syntax"></a>構文  
  
```xml  
<RequiredPlatformVersion> OperatingSystem </RequiredPlatformVersion>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 なし。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[TemplatePlatformName](../extensibility/templatedata-element-visual-studio-templates.md)|プロジェクト テンプレートの対象となるプラットフォームを指定します。|  
  
## <a name="text-value"></a>テキスト値  
 テキスト値が必要です。  
  
## <a name="remarks"></a>コメント  
 このテキストは、テンプレートで必要なオペレーティング システムの最小バージョンを指定します。  
  
## <a name="example"></a>例  
 次の例では、プロジェクト テンプレートで [!INCLUDE[win8](../debugger/includes/win8_md.md)] 以降が対象となるように指定しています。  
  
```xml  
<VSTemplate Type="Project" Version="3.0.0"    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <TargetPlatformName>Windows</TargetPlatformName>  
            <RequiredPlatformVersion>6.3.0</RequiredPlatformVersion>  
  
    </TemplateData>  
    <TemplateContent>  
  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>参照  
 [TargetPlatformName 要素 (Visual Studio テンプレート)](../extensibility/targetplatformname-element-visual-studio-templates.md)   
 [プロジェクトと項目テンプレートの作成](../ide/creating-project-and-item-templates.md)   
 [Visual Studio テンプレート スキーマ参照](../extensibility/visual-studio-template-schema-reference.md)