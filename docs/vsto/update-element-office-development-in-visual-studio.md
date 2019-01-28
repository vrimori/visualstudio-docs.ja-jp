---
title: '&lt;更新&gt;要素 (Visual Studio での Office 開発)'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- update element
- <update> element
- application manifests [Office development in Visual Studio], <update> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 461fae79e3af346d64017166b6dae3ace67599e1
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54867391"
---
# <a name="ltupdategt-element-office-development-in-visual-studio"></a>&lt;更新&gt;要素 (Visual Studio での Office 開発)
  `update`要素は、更新プログラムは、ソリューションを確認する間隔を指定します。

## <a name="syntax"></a>構文

```xml
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

 `update` 要素には、次の属性があります。

|属性|説明|
|---------------|-----------------|
|`enabled`|必須。 有効値は次のいずれかに設定します。<br /><br /> -   **true**更新プログラムを確認します。<br />-   **false**更新プログラムのチェックを回避します。|

 `update` 要素には、次の子要素があります。

### <a name="expiration"></a>expiration 
 `expiration` 要素は必須です。この要素は `vstav3` 名前空間に属します。 この要素は、更新プログラムのソリューションの確認間隔を指定します。

 `expiration` 要素には、次の属性があります。

|属性|説明|
|---------------|-----------------|
|`maximumAge`| 必須。 値は整数に設定します。|
|`unit`|必須。 設定`unit`値は次のいずれかに。<br /><br /> -   **時間**<br />-   **日**<br />-   **週**|

## <a name="example-of-always-checking-for-updates"></a>常に更新プログラムのチェックの例

### <a name="description"></a>説明
 次のコード例を示しています、`update`常に Office ソリューションの更新プログラムの確認に設定されている要素。

### <a name="code"></a>コード

```xml
<vstav3:update enabled="true" />
```

## <a name="example-of-setting-a-default-update-interval"></a>既定の更新間隔を設定する例

### <a name="description"></a>説明
 次のコード例を示しています、 `update` Office ソリューションに対するアプリケーション マニフェスト内の要素。 このコード例で示されている例の一部は、 [Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)します。

### <a name="code"></a>コード

```xml
<vstav3:update enabled="true">
    <vstav3:expiration maximumAge="7" unit="days" />
</vstav3:update>
```

## <a name="see-also"></a>関連項目

- [ClickOnce を使用して Office ソリューションを配置します。](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Office ソリューション用アプリケーション マニフェスト](../vsto/application-manifests-for-office-solutions.md)
- [Office ソリューション用配置マニフェストします。](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)
