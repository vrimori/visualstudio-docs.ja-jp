---
title: "&lt;更新&gt;要素 (Visual Studio での Office 開発) |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- update element
- <update> element
- application manifests [Office development in Visual Studio], <update> element
ms.assetid: bdd5dbf7-ddda-4ef6-9db5-1fb4405261a0
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1733ac8333675975bb5d4b42dce9df3c01e5ac0f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltupdategt-element-office-development-in-visual-studio"></a>&lt;更新&gt;要素 (Visual Studio での Office 開発)
  `update`要素は、更新プログラムのソリューションを確認する間隔を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
<update  
  enabled>  
  <expiration  
    maximumAge  
    unit  
  />  
</update>  
```  
  
## <a name="elements-and-attributes"></a>要素と属性  
 `update` 要素は必須です。この要素は `vstav3` 名前空間に属します。  
  
 `update`要素には、次の属性です。  
  
|属性|説明|  
|---------------|-----------------|  
|`enabled`|必須。 有効値は次のいずれかに設定します。<br /><br /> -   **true**更新プログラムを確認します。<br />-   **false**の更新プログラムをチェックしないようにします。|  
  
 `update`要素には、次の子要素です。  
  
### <a name="expiration"></a>有効期限  
 `expiration` 要素は必須です。この要素は `vstav3` 名前空間に属します。 この要素では、更新プログラムのソリューションをチェックする間隔を指定します。  
  
 `expiration`要素には、次の属性です。  
  
|属性|説明|  
|---------------|-----------------|  
|`maximumAge`|必須。 値は整数に設定します。|  
|`unit`|必須。 設定`unit`値は次のいずれかに。<br /><br /> -   **時間**<br />-   **日数**<br />-   **週**|  
  
## <a name="example-of-always-checking-for-updates"></a>常に更新プログラムのチェックの例  
  
### <a name="description"></a>説明  
 次のコード例を示しています、`update`常に Office ソリューションの更新プログラムの確認に設定されている要素です。  
  
### <a name="code"></a>コード  
  
```  
<vstav3:update enabled="true" />  
```  
  
## <a name="example-of-setting-a-default-update-interval"></a>既定の更新間隔を設定する例  
  
### <a name="description"></a>説明  
 次のコード例を示しています、 `update` Office ソリューションに対するアプリケーション マニフェストの要素。 このコード例は、「 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)」に記載されている例から一部を抜粋したものです。  
  
### <a name="code"></a>コード  
  
```  
<vstav3:update enabled="true">  
    <vstav3:expiration maximumAge="7" unit="days" />  
</vstav3:update>  
```  
  
## <a name="see-also"></a>参照  
 [ClickOnce を使用して Office ソリューションの配置](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Office ソリューション用配置マニフェスト](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce アプリケーション マニフェスト](/visualstudio/deployment/clickonce-application-manifest)  
  
  