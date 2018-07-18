---
title: コード分析を用いたチェックイン ポリシーに関するバージョンの互換性
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 01a8a0c4e859e6f03ba55176d535b0b4e7e6a1b0
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31915816"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>コード分析を用いたチェックイン ポリシーに関するバージョンの互換性
評価し、コード分析チェックイン ポリシーに異なるバージョンの使用を作成する必要がある場合[!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)]、方法の違いを理解する必要があります[!INCLUDE[vstsTfsOrcasLong](../code-quality/includes/vststfsorcaslong_md.md)]と[!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]チェックイン ポリシーを評価します。

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>チェックイン ポリシーを評価するためのバージョンの互換性

-   コード分析チェックイン ポリシーを評価するときに[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]、そのルールに含まれていた[!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]に存在しないが、[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]は無視されます。

-   コード分析チェックイン ポリシーを評価するときに[!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]に排他的であるすべての新しいルール[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]は無視されます。

-   コード分析チェックイン ポリシーは、規則アセンブリを指定した場合[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]ことが認識しないことのアセンブリが指定されているすべての規則は無視されます。

-   コード分析チェックイン ポリシーがルール アセンブリを指定するかどうかを[!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]認識されない、メッセージが表示されます。

## <a name="version-compatibility-for-authoring-check-in-policies"></a>チェックイン ポリシーを作成するためのバージョンの互換性

-   使用して、コード分析チェックイン ポリシーを作成するかどうか、[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]バージョンの[!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)]、使用することはできません、[!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]バージョンの[!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)]を修正します。 また、および[!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]ポリシーを評価することはできません。

-   使用して、コード分析チェックイン ポリシーを作成するかどうかは[!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)]で[!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]、使用することができます[!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)]で[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]、およびポリシーを変更することができますもで評価する[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]です。 使用して、ポリシーを変更した後[!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)]で[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]を使用して、ポリシーを編集できなく[!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)]で[!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]です。 [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] 厳密な名前の不一致を問題なくポリシーを評価できます。

-   コード分析チェックイン ポリシー設定で作成するルール両方に適用される[!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]と[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]でのポリシーを作成する必要があります[!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]、必要なすべての変更を行い、ポリシーを保存します。 場合にのみ規則への変更が存在[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]、変更してポリシーを保存する[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]です。

     ポリシーを保存した後に[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]に存在するルールの設定を変更することが不要になった[!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]のみです。