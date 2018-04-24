---
title: 'CA1900: 値型フィールドはポータブルでなければなりません'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1900
- ValueTypeFieldsShouldBePortable
helpviewer_keywords:
- ValueTypeFieldsShouldBePortable
- CA1900
ms.assetid: 1787d371-389f-4d39-b305-12b53bc0dfb9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 56c779095a68fc61c25412e6b895ea2bb5a635c3
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="ca1900-value-type-fields-should-be-portable"></a>CA1900: 値型フィールドはポータブルでなければなりません
|||
|-|-|
|TypeName|ValueTypeFieldsShouldBePortable|
|CheckId|CA1900|
|カテゴリ|Microsoft.Portability|
|互換性に影響する変更点|互換性に影響するの場合は、フィールドは、アセンブリ外見なすことができます。<br /><br /> 非区切りのフィールドがアセンブリの外側に表示されていない場合。|

## <a name="cause"></a>原因
 このルールは、明示的なレイアウトで宣言されている構造体が、64 ビット オペレーティング システムでアンマネージ コードにマーシャ リングするときに、適切にアライメントされるを確認します。 アライメントされていないメモリにアクセスし、この違反が修正されていない場合、プロセスがクラッシュ、ia-64 では許可されません。

## <a name="rule-description"></a>規則の説明
 64 ビット オペレーティング システムでクラッシュを発生ずれているフィールドを含む明示的なレイアウトを含む構造体。

## <a name="how-to-fix-violations"></a>違反の修正方法
 複数オフセット 8 の倍数である必要がありますか、そのサイズの倍数であるオフセットとフィールドは 8 バイト、8 バイト未満であるすべてのフィールドがあります。 別のソリューションは、使用する`LayoutKind.Sequential`の代わりに`LayoutKind.Explicit`妥当な場合は、します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 エラーの発生した場合にのみ、この警告を抑制する必要があります。