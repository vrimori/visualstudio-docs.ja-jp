---
title: '方法: メニュー項目を使用した警告の抑制 |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- warnings, suppressing
- code analysis, suppressing warnings
ms.assetid: 36bd1850-dcde-4ed0-9bc3-0b83df434362
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1c756a5ab6516d78f5370622555898c98658e8b3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49211788"
---
# <a name="how-to-suppress-warnings-by-using-the-menu-item"></a>方法: メニュー項目を使用して警告を抑制する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

注]
>  ソース内抑制は web サイト プロジェクトのサポートされていません。  
  
 コード分析 ウィンドウを使用して、コード分析の警告を抑制することができます。 警告の抑制は、無効にすることと同じではありません。 警告を抑制する場合は、違反の特定のインスタンスにのみ適用されます。 エラー一覧 ウィンドウで同じ警告の他の違反も報告されます。  
  
 コード分析を実行した後、1 つ以上のコード分析 ウィンドウに表示されるコード分析の警告には適用されません、アプリケーションを決定可能性があります。 たとえば、コードが正しいことを判断可能性があります。 または、違反の重大低優先度、現在の開発サイクルで修正される予定はない場合があります。 どのような理由は、警告が、コードが確認されたことと、警告を抑制することが決定されました、チーム メンバーに該当しないことを示す頻繁に便利です。 ソース内抑制は、警告が生成される場所の近くに抑制を配置することができるので便利です。  
  
 ソース コードや、グローバル抑制ファイルで、抑制に表示されるかどうかを選択できます。 グローバル抑制ファイルには、いくつかの抑制を配置する必要があります。 この場合は、**でソース**オプションは無効になります。  
  
### <a name="to-suppress-a-warning-by-using-menu-item"></a>メニュー項目を使用して警告を抑制するには  
  
1.  **分析**] メニューの [選択**Windows**選び、**コード分析**します。  
  
2.  **コード分析**ウィンドウで、警告の抑制を選択します。  
  
3.  アクションを選択し、選択**メッセージの抑制**、いずれかを選択し、**でソース**または**プロジェクト抑制ファイル内**します。  
  
     特定の警告が抑制されに取り消し線付きのコード分析 ウィンドウで、警告が表示されます。  
  
> [!NOTE]
>  グローバル抑制ファイル内のターゲットがない抑制が表示されます。



