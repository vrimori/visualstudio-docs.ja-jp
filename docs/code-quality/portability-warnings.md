---
title: "移植性に関する警告 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.PortabilityRules
helpviewer_keywords:
- portability warnings
- managed code analysis warnings, portability warnings
- warnings, portability
ms.assetid: 902e859a-2153-4970-baaa-8a5b4a11806f
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 112f3686f2a3d21b2d5d493498b42e9b63fdb05b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="portability-warnings"></a>移植性に関する警告
移植性に関する警告は、さまざまなオペレーティング システムでの移植性をサポートします。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|ルール|説明|  
|----------|-----------------|  
|[CA1900: 値型フィールドはポータブルでなければなりません](../code-quality/ca1900-value-type-fields-should-be-portable.md)|このルールは、明示的なレイアウト属性を使用して宣言されている構造体が、64 ビット オペレーティング システムでアンマネージ コードにマーシャ リングするときに、適切にアライメントされるを確認します。|  
|[Ca 1901: P/invoke 宣言はポータブルでなければなりません](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|このルールは、各パラメーターのサイズと、P/invoke の戻り値が評価され、そのサイズが 32 ビットおよび 64 ビットのオペレーティング システムでアンマネージ コードにマーシャ リングするときに正しいことを確認します。|  
|[CA1903: 対象のフレームワークから API のみを使用します](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|メンバーまたは型が、プロジェクトの対象のフレームワークに含まれていない Service Pack で導入されたメンバーまたは型を使用しています。|