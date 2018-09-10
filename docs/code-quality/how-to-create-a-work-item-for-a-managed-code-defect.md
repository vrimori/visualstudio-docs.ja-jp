---
title: '方法: マネージド コードの障害に対する作業項目を作成する'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- managed code, creating work items for code defects
- code analysis, creating work items
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: b251970bfd57b31842e1573e2e156e11a517c81a
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2018
ms.locfileid: "44279476"
---
# <a name="how-to-create-a-work-item-for-a-managed-code-defect"></a>方法: マネージド コードの障害に対する作業項目を作成する

Visual Studio 内から、作業項目をログには、作業項目追跡機能を使用することができます。 この機能を使用するプロジェクトの Azure DevOps プロジェクトを含める必要があります[!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)]します。

## <a name="to-create-a-work-item-for-managed-code-defect"></a>マネージ コードの障害に対する作業項目を作成するには

1. **コード分析**ウィンドウで、警告を選択します。

2. 選択**アクション**を選択し、**作業項目の作成**し作成する作業項目の種類を選択します。

     欠陥の情報を指定するための新しい作業項目が作成されます。

## <a name="to-create-a-work-item-for-multiple-managed-code-defects"></a>複数の作業項目を作成するには、マネージ コードの不具合

1. **エラー一覧**を複数の警告を選択し、警告を右クリックします。

2. をポイント**作業項目の作成**を作成する作業項目の種類をクリックします。

     選択したすべての警告バグ情報を指定するための単一の作業項目が作成されます。