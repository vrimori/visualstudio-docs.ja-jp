---
title: 移植性に関する警告 |Microsoft Docs
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
- vs.codeanalysis.PortabilityRules
helpviewer_keywords:
- portability warnings
- managed code analysis warnings, portability warnings
- warnings, portability
ms.assetid: 902e859a-2153-4970-baaa-8a5b4a11806f
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 03ae0c7ea743379754eac7c40f86f26a3244f709
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47544300"
---
# <a name="portability-warnings"></a>移植性に関する警告
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[移植性に関する警告](https://docs.microsoft.com/visualstudio/code-quality/portability-warnings)します。  
  
移植性に関する警告は、さまざまなオペレーティング システムでの移植性をサポートします。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|ルール|説明|  
|----------|-----------------|  
|[CA1900: 値型フィールドはポータブルでなければなりません](../code-quality/ca1900-value-type-fields-should-be-portable.md)|このルールは、明示的なレイアウト属性を使用して宣言された構造体が、64 ビット オペレーティング システムのアンマネージ コードにマーシャ リングするときに、適切にアライメントされるかを確認します。|  
|[CA1901: P/Invoke 宣言はポータブルでなければなりません](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|このルールでは、各パラメーターのサイズと、P/invoke の戻り値が評価され、サイズが 32 ビットと 64 ビットのオペレーティング システムのアンマネージ コードにマーシャ リングするときに正しいことを確認します。|  
|[CA1903: 対象のフレームワークから API のみを使用します](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|メンバーまたは型が、プロジェクトの対象のフレームワークに含まれていない Service Pack で導入されたメンバーまたは型を使用しています。|



