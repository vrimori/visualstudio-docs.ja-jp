---
title: 'Ca 1900: 値型フィールドはポータブルでなければなりません。Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1900
- ValueTypeFieldsShouldBePortable
helpviewer_keywords:
- ValueTypeFieldsShouldBePortable
- CA1900
ms.assetid: 1787d371-389f-4d39-b305-12b53bc0dfb9
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b0a636c1de245aa46adb0b0e43c6802dddf57810
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47548532"
---
# <a name="ca1900-value-type-fields-should-be-portable"></a>CA1900: 値型フィールドはポータブルでなければなりません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 2017 の最新ドキュメントについては、次を参照してください。 [ca 1900: 値型フィールドはポータブルでなければなりません](https://docs.microsoft.com/visualstudio/code-quality/ca1900-value-type-fields-should-be-portable)docs.microsoft.com でリリースされました。  
  
|||  
|-|-|  
|TypeName|ValueTypeFieldsShouldBePortable|  
|CheckId|CA1900|  
|カテゴリ|Microsoft.Portability|  
|互換性に影響する変更点|– 場合、アセンブリの外側にフィールドを確認できます。<br /><br /> 改行のフィールドが、アセンブリの外部に表示されない場合。|  
  
## <a name="cause"></a>原因  
 このルールは、明示的なレイアウトで宣言された構造体が、64 ビット オペレーティング システムのアンマネージ コードにマーシャ リングするときに、適切にアライメントされるかを確認します。 Ia-64 では、アラインされていないメモリにアクセスし、この違反が固定されていない場合、プロセスがクラッシュは許可されません。  
  
## <a name="rule-description"></a>規則の説明  
 構造体で明示的なレイアウトを含む 64 ビット オペレーティング システムでクラッシュするフィールドの不整合が発生します。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 詳細はオフセットが 8 の倍数である必要があります。 または 8 バイト未満であるすべてのフィールドはオフセット、サイズの倍数である、および 8 バイトであるフィールドにあります。 別のソリューションは、使用する`LayoutKind.Sequential`の代わりに`LayoutKind.Explicit`妥当な場合は、します。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 エラーが発生した場合にのみ、この警告を抑制する必要があります。

