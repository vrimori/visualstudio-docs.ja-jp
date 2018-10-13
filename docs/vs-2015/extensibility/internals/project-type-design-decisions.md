---
title: プロジェクトの種類の設計上の決定 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project types, project file persistence
- project types, commitment mechanics
- project types, items
- project types, design decisions
ms.assetid: f68671fe-fd7a-4e56-a0b5-330b0f1fedb1
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9b5738f3119a8e5f1f6c1d8cb3ee47d64df1541d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49195482"
---
# <a name="project-type-design-decisions"></a>プロジェクト タイプのデザインの方針
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

新しいプロジェクトの種類を作成する前に、プロジェクトの種類に関するいくつかの設計上の決定を行う必要があります。 使用して、プロジェクトに含まれる項目、プロジェクト ファイルの保存方法、およびどのようなコミットメント モデルの種類を決定する必要があります。  
  
## <a name="project-items"></a>プロジェクト項目  
 プロジェクトでは、ファイルまたは抽象オブジェクトを使用しますか。 ファイルを使用する場合は、それが参照に基づくまたはディレクトリ ベースのファイル ローカルまたはリモートにあるファイルまたは実行の抽象オブジェクトか?  
  
 プロジェクト内の項目は、ファイル、または、インターネット経由でデータベースのリポジトリまたはデータ接続内のオブジェクトより抽象的オブジェクトができます。 項目がファイルの場合は、プロジェクト参照に基づくまたはディレクトリ ベースのプロジェクトのいずれかにすることができます。  
  
 参照ベースのプロジェクトでは、項目が 1 つ以上のプロジェクトに表示できます。 ただし、項目が表す実際のファイルは、1 つのディレクトリのみであります。 ディレクトリ ベースのプロジェクトでは、すべてのプロジェクト項目は、ディレクトリ構造に存在します。 詳細については、次を参照してください。[プロジェクトにおける NIB: 項目の管理](http://msdn.microsoft.com/en-us/762e606b-7f44-4b66-97a1-e30a703654a0)します。  
  
 ローカル項目は、アプリケーションがインストールされている同じコンピューターに格納されます。 リモートの項目は、ローカル ネットワークでは、別のサーバーまたは別の場所はインターネット上に格納できます。  
  
## <a name="project-file-persistence"></a>プロジェクト ファイルの永続化  
 一般的なフラット ファイル システムまたは構造化ストレージ、データは格納されますか。 標準のエディターまたはプロジェクト固有のエディターを使用してファイルを開きますか。  
  
 データを保持するには、ほとんどのアプリケーションはファイルでは、そのデータを保存し、ユーザーが確認する必要がありますまたは情報を変更するときに読むこと。  
  
 構造化ストレージ、複合ファイルとも呼ばれます。 は通常、いくつかのコンポーネント オブジェクト モデル (COM) オブジェクトを 1 つのファイルに永続化されたデータを格納する必要がある場合に使用されます。 構造化ストレージ、いくつかの異なるソフトウェア コンポーネントは 1 つのディスク ファイルを共有できます。  
  
 プロジェクト内の項目の永続性に関して考慮すべきいくつかのオプションがあります。 次のオプションのいずれかを実行できます。  
  
-   変更されると、各ファイルを個別に保存します。  
  
-   1 つの多くのトランザクションをキャプチャ**保存**操作。  
  
-   ファイルをローカルに保存をサーバーにパブリッシュしたり、アイテムは、リモート オブジェクトへのデータ接続を表す場合に、プロジェクト項目を保存するための別のアプローチを使用してキーを押します。  
  
 永続化の詳細については、次を参照してください。[プロジェクトの永続化](../../extensibility/internals/project-persistence.md)と[とプロジェクト項目の保存](../../extensibility/internals/opening-and-saving-project-items.md)します。  
  
## <a name="project-commitment-model"></a>コミットメントのプロジェクト モデル  
 永続化されたデータ オブジェクトが開かれるダイレクト モードまたはトランザクション モードにしますか?  
  
 データ オブジェクトが直接モードで開かれると、データに加えられた変更は、ユーザーが手動でファイルを保存すると、またはすぐに組み込まれます。  
  
 トランザクション モードを使用してデータ オブジェクトが開かれると、変更はメモリに一時的な場所に保存され、ユーザーが手動でファイルの保存を選択するまではコミットされません。 その時点では、すべての変更はまとめて行う必要があります。 または変更は行われません。  
  
## <a name="see-also"></a>関連項目  
 [チェックリスト: 新しいプロジェクトの種類を作成します。](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [プロジェクトにおける NIB: 項目の管理](http://msdn.microsoft.com/en-us/762e606b-7f44-4b66-97a1-e30a703654a0)   
 [開くと、プロジェクト項目の保存](../../extensibility/internals/opening-and-saving-project-items.md)   
 [プロジェクトの永続化](../../extensibility/internals/project-persistence.md)   
 [プロジェクト モデルの要素](../../extensibility/internals/elements-of-a-project-model.md)   
 [プロジェクト モデルのコア コンポーネント](../../extensibility/internals/project-model-core-components.md)   
 [プロジェクト タイプの作成](../../extensibility/internals/creating-project-types.md)

