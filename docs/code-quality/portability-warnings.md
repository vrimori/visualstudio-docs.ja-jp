---
title: 移植性に関する警告
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- vs.codeanalysis.PortabilityRules
helpviewer_keywords:
- portability warnings
- managed code analysis warnings, portability warnings
- warnings, portability
ms.assetid: 902e859a-2153-4970-baaa-8a5b4a11806f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 81f463656894b9c6a9c13b28560ad310eaa6c9df
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="portability-warnings"></a>移植性に関する警告
移植性に関する警告は、さまざまなオペレーティング システムでの移植性をサポートします。

## <a name="in-this-section"></a>このセクションの内容

|ルール|説明|
|----------|-----------------|
|[CA1900: 値型フィールドはポータブルでなければなりません](../code-quality/ca1900-value-type-fields-should-be-portable.md)|このルールは、明示的なレイアウト属性を使用して宣言されている構造体が、64 ビット オペレーティング システムでアンマネージ コードにマーシャ リングするときに、適切にアライメントされるを確認します。|
|[Ca 1901: P/invoke 宣言はポータブルでなければなりません](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|このルールは、各パラメーターのサイズと、P/invoke の戻り値が評価され、そのサイズが 32 ビットおよび 64 ビットのオペレーティング システムでアンマネージ コードにマーシャ リングするときに正しいことを確認します。|
|[CA1903: 対象のフレームワークから API のみを使用します](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|メンバーまたは型が、プロジェクトの対象のフレームワークに含まれていない Service Pack で導入されたメンバーまたは型を使用しています。|