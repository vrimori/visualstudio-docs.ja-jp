---
title: 'DA0030: データベース プロジェクトの階層の相互作用の測定を収集します。 | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.DA0030
- vs.performance.rules.DA0030
- vs.performance.30
ms.assetid: 42b2f69d-0cfa-4854-82c4-589c3d8b4557
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 16d6275074b3cae6b186fe9bb113e32c33e284af
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51796754"
---
# <a name="da0030-gather-tier-interaction-measurements-for-database-projects"></a>DA0030: データベース プロジェクトの階層の相互作用の測定を収集します。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

規則 Id |DA0030 |  
|カテゴリ |プロファイリング ツールの使用 |  
|プロファイル方法 |サンプリング |  
|メッセージ |多階層アプリケーションの相互作用の測定を収集、データベースの使用パターンと重要なデータを理解するのに役立ちますアクセス遅延が発生します。 階層相互作用プロファイリング オプションを有効にもう一度アプリケーションをプロファイリングを試みてください |。  
|規則の種類 |情報 |  
  
## <a name="cause"></a>原因  
 <xref:System.Data> メソッドの呼び出しがプロファイル データの大きな割合を占めているため、プロファイリングの実行中に階層の相互作用データが収集されませんでした。 プロファイリングを再度実行し、階層の相互作用データを追加することを検討してください。  
  
## <a name="rule-description"></a>規則の説明  
 この規則は、System.Data 名前空間 (<xref:System.Data.Linq><xref:System.Data.Linq> を含む) に常駐する関数内で、重要なアクティビティが発生するたびに適用されます。  
  
 多階層アプリケーションは、アプリケーションのプレゼンテーションとデータ レイヤー用に複数層のサービスを使用します。 多くの場合、データ レイヤーは、Microsoft SQL Server などのデータベース管理システムを実行する独立したプロセスです。 データ レイヤーは、個別のコンピューター上でアプリケーションの途中から実行することもできます。 サンプリング プロファイルの場合、アウトプロセスまたはリモートで実行されるサービスや関数の内部まで詳しく確認することはできません。  
  
 プロファイリング ツールで ADO.NET サービスへの非同期呼び出しを使用すると、Microsoft SQL Server のデータ レイヤーとの対話を行う多階層アプリケーションのタイミング情報を収集できます。 その場合、[階層の相互作用のプロファイルを有効にする] オプションを有効にする必要があります。 このオプションは、既定ではオフになっています。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則は情報提供用であるため、是正措置は必要ない場合があります。  
  
 Visual Studio IDE から階層の相互作用データをプロファイル データに追加する方法については、「[階層相互作用データの収集](../profiling/collecting-tier-interaction-data.md)」を参照してください。 コマンド ラインから階層の相互作用データを追加する方法の詳細については、「[階層相互作用データの収集](../profiling/adding-tier-interaction-data-from-the-command-line.md)」を参照してください。



