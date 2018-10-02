---
title: データの保存 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DataRow.RowState
- DataSet.GetChanges
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- DBDirect methods
- updating data
- data [Visual Studio], saving
- TableAdapter DBDirect methods
- databases, updating
- TableAdapter.Update method
- data [Visual Studio], updating
- saving data
- updating databases
ms.assetid: 21d2b115-62e4-4ac9-a873-dcbb535b8af8
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 14ff0e62608c3e2ab0c72366d9544f1d1309737a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47547621"
---
# <a name="saving-data"></a>データの保存
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

データの保存は、元のデータ ストア、通常は SQL Server などのリレーショナル データベースに永続化のプロセスがアプリケーションのデータ モデル内のデータを変更します。  
  
 データ モデルを使用してデータ ソースの更新は、2 段階のプロセスでは通常です。 新しい情報でデータ モデルを更新するには、まず、新しいレコードが変更されたレコード、または削除されたレコード。 2 番目の手順では、元のデータベースにデータ モデルに変更を保存します。  
  
 次のトピックでは、概念とデータの保存に関連するタスクについて説明します。  
  
## <a name="related-topics"></a>関連トピック  
 [データをデータベースに保存する](../data-tools/save-data-back-to-the-database.md)  
 データセットの変更を加える方法と、データベースにそれらの変更を保存するには、データセットが変更に関する情報を追跡する方法の概要を示します。  
  
 [エンティティ データの保存](../data-tools/saving-entity-data.md)  
 変更を保存する方法について説明します[ADO.NET Entity Framework](http://msdn.microsoft.com/library/a437041f-6899-4ae7-96ce-aabf528d7205)と[WCF データ サービスの 4.5](http://msdn.microsoft.com/library/73d2bec3-7c92-4110-b905-11bb0462357a)アプリケーション。