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
ms.openlocfilehash: 5d04ac68140395cbc2dae9bd70f57e587d9b7732
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49898233"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>コード分析を用いたチェックイン ポリシーに関するバージョンの互換性

評価およびコード分析チェックイン ポリシーの異なるバージョンを使用して作成する必要がある場合[!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)]、方法の違いを理解する必要があります[!INCLUDE[vstsTfsOrcasLong](../code-quality/includes/vststfsorcaslong_md.md)]と[!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]チェックイン ポリシーを評価します。

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>チェックイン ポリシーを評価するためのバージョンの互換性

- コード分析チェックイン ポリシーが評価されるタイミング[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]、任意のルールに存在していた[!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]に存在しないが、[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]は無視されます。

- コード分析チェックイン ポリシーが評価されるタイミング[!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]にのみ含まれているすべての新しいルール[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]は無視されます。

- コード分析チェックイン ポリシー、規則アセンブリを指定する場合[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]では認識されないアセンブリで指定されているすべての規則は無視されます。

- コード分析チェックイン ポリシーがルール アセンブリを指定するかどうかを[!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]認識しないメッセージが表示されます。

## <a name="version-compatibility-for-authoring-check-in-policies"></a>チェックイン ポリシーを作成するためのバージョンの互換性

- 使用して、コード分析チェックイン ポリシーを作成するかどうか、[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]バージョンの[!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)]、使用することはできません、[!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]バージョンの[!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)]を修正する方法。 また、[!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]ポリシーを評価することはできません。

- 使用して、コード分析チェックイン ポリシーを作成するかどうかは[!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)]で[!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]、使用することができます[!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)]で[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]、およびポリシーを変更することができますもによって評価される[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]します。 使用して、ポリシーを変更した後[!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)]で[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]を使用して、ポリシーを編集できなく[!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)]で[!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]します。 [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] 厳密な名前の不一致が問題なくポリシーを評価できます。

- 両方に適用されるルールの設定でコード分析チェックイン ポリシーを作成する[!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]と[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]のポリシーを作成する必要があります[!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]、必要に応じて、すべての変更を行うし、ポリシーを保存します。 規則に対する変更にのみ存在する場合[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]、変更のポリシーを保存して[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]します。

   後でポリシーを保存する[!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]、内に存在する規則の設定を変更できなく[!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]のみです。