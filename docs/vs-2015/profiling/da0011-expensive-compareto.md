---
title: 'DA0011: CompareTo の負荷が高くなっています | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.DA0011
- vs.performance.rules.DAExpensiveCompareTo
- vs.performance.11
- vs.performance.rules.DA0011
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0726ef4eb93d3e962e5fa39fe9cc7acbdbfbe8ca
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49210445"
---
# <a name="da0011-expensive-compareto"></a>DA0011: CompareTo の負荷が高くなっています
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 2017 の最新ドキュメントについては、次を参照してください。 [DA0011: CompareTo の負荷が](https://docs.microsoft.com/visualstudio/profiling/da0011-expensive-compareto)docs.microsoft.com でリリースされました。  
  
|||  
|-|-|  
|規則 ID|DA0011|  
|カテゴリ|.NET Framework の使用|  
|プロファイル方法|サンプリング<br /><br /> .NET メモリ|  
|メッセージ|CompareTo 関数の負荷を抑える必要があります。メモリを割り当てることはできません。 可能な場合は、CompareTo 関数の複雑さを軽減してください。|  
|規則の種類|警告|  
  
## <a name="cause"></a>原因  
 型の CompareTo メソッドが高コストであるか、またはメモリを割り当てています。  
  
## <a name="rule-description"></a>規則の説明  
 CompareTo メソッドは効率的にする必要があります。メモリを割り当てることはできません。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 CompareTo メソッドの複雑さを軽減してください。

