---
title: "方法: メニュー項目を使用して警告を抑制する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- warnings, suppressing
- code analysis, suppressing warnings
ms.assetid: 36bd1850-dcde-4ed0-9bc3-0b83df434362
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a197170285a8f8a9d3f0cc01638557f30fd1f126
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-suppress-warnings-by-using-the-menu-item"></a>方法: メニュー項目を使用して警告を抑制する
> [!NOTE]
>  ソース内抑制は web サイト プロジェクトのサポートされていません。  
  
 コード分析 ウィンドウを使用するコード分析の警告を抑制することができます。 警告を抑制するは、無効にすることと同じではありません。 警告を抑制する場合は、違反の特定のインスタンスにのみ適用されます。 エラー一覧 ウィンドウで、同じ警告の他の違反も報告されます。  
  
 コード分析を実行した後、コード分析 ウィンドウに表示されるコード分析の警告の 1 つ以上いないことをアプリケーションに適用可能なを指定可能性があります。 たとえば、コードが正しいことがわかった場合があります。 または、いくつかの違反低優先度、固定で現在の開発サイクルはない場合があります。 その理由に関係なく警告は、コードが確認されたされことが決定される警告を抑制することがわかっている場合、チーム メンバーに該当しないことを示すために頻繁に便利です。 ソース内抑制は、警告を生成する場所の近くに抑制を配置することができるため便利です。  
  
 ソース コードや、グローバル抑制ファイルで抑制を記述するかどうかを選択できます。 グローバル抑制ファイルに抑制を配置する必要があります。 このような場合、**でソース**オプションは無効になります。  
  
### <a name="to-suppress-a-warning-by-using-menu-item"></a>メニュー項目を使用して警告を抑制するには  
  
1.  **分析**] メニューの [選択**Windows**を選択し**コード分析**です。  
  
2.  **コード分析** ウィンドウで、警告を抑制するを選択します。  
  
3.  アクションをクリックし、選択**メッセージの抑制**、いずれかを選択し**でソース**または**プロジェクト抑制ファイル内**です。  
  
     特定の警告を抑制すると、および取り消し線付きコード分析 ウィンドウで、警告が表示されます。  
  
> [!NOTE]
>  グローバル抑制ファイル内のターゲットがない抑制が表示されます。