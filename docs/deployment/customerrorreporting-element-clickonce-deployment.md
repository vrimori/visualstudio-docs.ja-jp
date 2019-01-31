---
title: '&lt;customErrorReporting&gt;要素 (ClickOnce 配置) |Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <customErrorReporting> element [ClickOnce deployment manifest]
ms.assetid: 7d31816e-c692-46b5-9cc9-753284b3bcda
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7254f5735be3efa45b7ba3be0541996cb6c2cc69
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54997638"
---
# <a name="ltcustomerrorreportinggt-element-clickonce-deployment"></a>&lt;customErrorReporting&gt;要素 (ClickOnce 配置)
エラー発生時に表示する URI を指定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
<customErrorReporting  
   uri  
/>  
```  
  
## <a name="remarks"></a>コメント  
 この要素は省略可能です。 これがない[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]例外スタックを示すエラー ダイアログ ボックスが表示されます。 場合、`customErrorReporting`要素が存在する場合は、[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]によって示される URI が代わりに表示されます、`uri`パラメーター。 ターゲット URI では、外側の例外クラス、内部例外クラス、および内部例外メッセージをパラメーターとして含まれます。  
  
 この要素を使用すると、アプリケーションにエラー レポート機能を追加できます。 生成された URI には、エラーの種類に関する情報が含まれているために、Web サイトは、その情報と、適切なトラブルシューティング画面などの表示に解析できます。  
  
## <a name="example"></a>例  
 次の例では、`customErrorReporting`要素と共に生成された URI が生じる可能性があります。  
  
```xml
<customErrorReporting uri=http://www.contoso.com/applications/error.asp />  
  
Example Generated Error:  
http://www.contoso.com/applications/error.asp? outer=System.Deployment.Application.InvalidDeploymentException&&inner=System.Deployment.Application.InvalidDeploymentException&&msg=The%20application%20manifest%20is%20signed,%20but%20the%20deployment%20manifest%20is%20unsigned.%20Both%20manifests%20must%20be%20either%20signed%20or%20unsigned.  
```  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce 配置マニフェスト](../deployment/clickonce-deployment-manifest.md)