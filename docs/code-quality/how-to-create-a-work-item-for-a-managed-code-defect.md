---
title: '方法: マネージ コードの障害に対する作業項目を作成する'
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
ms.openlocfilehash: fcbb7716d8ba0496d267f3c8757bb8425884cfb0
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31918962"
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