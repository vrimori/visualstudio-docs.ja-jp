---
title: '方法: マネージ コードの障害に対する作業項目を作成する'
ms.date: 11/04/2016
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
ms.openlocfilehash: 41e4a507015a630eb31c86048e785ea179899ccf
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-create-a-work-item-for-a-managed-code-defect"></a>方法: マネージ コードの障害に対する作業項目を作成する

Visual Studio 内から、作業項目をログには、作業項目追跡機能を使用することができます。 この機能を使用するプロジェクトがチーム プロジェクトの一部をする必要があります[!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)]です。

## <a name="to-create-a-work-item-for-managed-code-defect"></a>マネージ コードの障害に対する作業項目を作成するには

1. **コード分析** ウィンドウで、警告を選択します。

2. 選択**アクション**、順に選択**作業項目の作成**作成する作業項目の種類を選択します。

     障害情報を指定するための新しい作業項目が作成されます。

## <a name="to-create-a-work-item-for-multiple-managed-code-defects"></a>複数のマネージ コード障害に対する作業項目を作成するには

1. **エラー一覧**、複数の警告を選択し、警告を右クリックします。

2. 指す**作業項目の作成**作成する作業項目の種類をクリックします。

     単一の作業項目、バグ情報を指定するための選択されたすべての警告が作成されます。