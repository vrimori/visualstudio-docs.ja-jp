---
title: '方法: マネージド コードの障害に対する作業項目を作成する'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- managed code, creating work items for code defects
- code analysis, creating work items
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1cb63612194148b5f3ea1f90d7c57e59fb84edbc
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54941828"
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