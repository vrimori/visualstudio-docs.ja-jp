---
title: データ クラスの継承 (O/R デザイナー) |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af32653c-f4e6-4217-8c5a-e32b322b4918
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c361d35a4c5d6c4418a803b6bbba403e5571e1e2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533677"
---
# <a name="data-class-inheritance-or-designer"></a>データ クラスの継承 (O/R デザイナー)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[データ クラスの継承 (O/R デザイナー)](https://docs.microsoft.com/visualstudio/data-tools/data-class-inheritance-o-r-designer)します。  
  
  
[!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] クラスは、他のオブジェクトと同様に、継承を使用して他のクラスから派生できます。 コードでは、あるクラスが別のクラスから継承されていることを宣言することによって、オブジェクト間の継承関係を指定できます。 データベースでは、継承関係が複数の方法で作成されます。 [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) では、一般にリレーショナル システムで実装されている単一テーブル継承の概念がサポートされます。  
  
 単一テーブル継承では、基本クラスと派生クラスの両方の列が入った単一データベース テーブルが関係します。 リレーショナル データでは、識別子の列に、特定のレコードが属するクラスを決定する値が含まれます。 たとえば、会社に採用されたすべての人を含む Persons テーブルについて考えます。 従業員の人もいれば、管理者の人もいます。 Persons テーブルには、Type という列があり、この列の値は管理者は 1、従業員は 2 です。 Type 列は識別子の列です。 このシナリオでは、従業員のサブクラスを作成して、そのクラスには Type の値が 2 であるレコードだけを入れるようにすることができます。  
  
 構成するときの継承エンティティ クラスを使用して、 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]、2 回、デザイナーに、継承データを含む 1 つのテーブルをドラッグします。 継承階層内の各クラスに 1 回です。 デザイナーにテーブルを追加した後に接続から継承項目、**オブジェクト リレーショナル デザイナー**ツールボックスし、4 つのセットの継承プロパティで、**プロパティ**ウィンドウ。  
  
## <a name="inheritance-properties"></a>継承プロパティ  
 継承プロパティとその説明については、次の表を参照してください。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|識別子プロパティ|現在のレコードが属するクラスを判別するプロパティ (列にマップされる)。|  
|基本クラスの識別子の値|レコードが基本クラスに属することを決定する、識別子プロパティとして指定された列の値。|  
|派生クラスの識別子の値|レコードが派生クラスに属することを決定する、識別子プロパティとして指定されたプロパティの値。|  
|継承の既定値|クラスとして指定されているプロパティの値に設定する必要があります、**識別子プロパティ**いずれかと一致しない、 **Base Class Discriminator Value**または**クラスの派生識別子の値**します。|  
  
 継承を使用し、リレーショナル データに対応するオブジェクト モデルの作成は、混乱しやすい場合があります。 このトピックでは、継承を構成する場合に必要な基本的な概念と個々のプロパティについて説明します。 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] による継承の構成方法についての詳しい説明については、以下のトピックを参照してください。  
  
|トピック|説明|  
|-----------|-----------------|  
|[方法: O/R デザイナーを使用して継承を構成する](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)|[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]を使用して単一テーブル継承を使用するエンティティ クラスを構成する方法について説明します。|  
|[チュートリアル: 単一テーブル継承を使用した LINQ to SQL クラスの作成 (O/R デザイナー)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)|[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]を使用して単一テーブル継承を使用するエンティティ クラスを構成するための詳細な手順を説明します。|  
  
## <a name="see-also"></a>関連項目  
 [LINQ to Visual Studio での SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [チュートリアル: LINQ to SQL クラス (O/R デザイナー) を作成します。](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [チュートリアル: 単一テーブル継承 (O/R デザイナー) を使用して LINQ to SQL クラスを作成します。](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)   
 [はじめに](http://msdn.microsoft.com/library/db8a557a-fef8-4f4f-bb91-8cff7250ee25)

