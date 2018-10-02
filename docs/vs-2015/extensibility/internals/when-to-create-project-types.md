---
title: プロジェクトの種類を作成する場合 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project types, conditions for creating
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8c99aed424094d21fa1cd84163d5ee36f206fa19
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47546044"
---
# <a name="when-to-create-project-types"></a>プロジェクト タイプを作成する状況
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[プロジェクトの種類を作成するときに](https://docs.microsoft.com/visualstudio/extensibility/internals/when-to-create-project-types)します。  
  
カスタマイズするため、単位を提供する新しいプロジェクトの種類を作成する[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]ユーザー向けです。 ただし、新しいプロジェクトの種類を作成する必要はありませんすべての[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]カスタマイズします。 次のガイドラインを使用するとは新しいプロジェクトの種類が、シナリオに必要かどうかを判断できます。  
  
## <a name="create-a-new-project-type"></a>新しいプロジェクトの種類を作成します。  
 カスタマイズする場合は、プロジェクトの種類を作成する必要があります[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]の次の方法の 1 つ以上を実行します。  
  
-   ビルドに参加、デプロイ、構成、およびソース管理。  
  
-   デバッグのサポートを提供します。  
  
-   プロジェクト アイテムの表示**ソリューション エクスプ ローラー**します。  
  
-   使用して、**プロジェクトを開く**または**新しいプロジェクト** ダイアログ ボックス。  
  
-   プロジェクトの入れ子をサポートします。  
  
## <a name="extend-an-existing-project-type"></a>既存のプロジェクトの種類を拡張します。  
 使用できる新しいプロジェクトの種類を作成したい場合があります[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]変更または既存のプロジェクトの種類の動作を拡張する次の方法でのビルド プロセスを変更するなど、[!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]プロジェクト。  
  
-   1 つの単位として複数のファイルを使用します。  
  
-   サブ項目の階層として 1 つのファイルを表示します。  
  
-   エディターの周囲のコマンドのコンテキストを表示します。  
  
-   エディターに対し、サービス コンテキストを表示します。  
  
## <a name="use-an-existing-project-type"></a>既存のプロジェクトの種類を使用して、  
 新しいプロジェクトを作成する必要がありますされません。 次の表では、プロジェクトの種類を作成する必要はありませんが、タスクを示します。  
  
|タスク|説明|  
|----------|-----------------|  
|コマンドの処理|すべての VSPackage では、コマンドを処理できます。|  
|エディターの構築|カスタム エディターを登録することができます。 詳細については、次を参照してください。[ドキュメント Windows およびエディター](http://msdn.microsoft.com/en-us/603625e1-62b6-413a-bc44-089346e166bc)します。|  
|Windows を所有しています。|新しいプロジェクトの種類を追加せず、両方のツールとドキュメント ウィンドウを作成できます。|  
|[プロパティ] ウィンドウでプロパティを公開します。|すべてのオブジェクトには、プロパティを公開できます。|  
  
## <a name="create-a-project-subtype"></a>プロジェクト サブタイプを作成します。  
 プロジェクト サブタイプを使用して、新しいプロジェクトの種類を作成することがなく、マネージ プロジェクトの種類を拡張することができます。 プロジェクト サブタイプでは、COM の集計を使用して、Microsoft で記述されたマネージ プロジェクトを拡張する[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]または[!INCLUDE[csprcs](../../includes/csprcs-md.md)]します。 COM の集計を含むマネージ プロジェクト システムの実装の大部分を再利用し、集計と、インターフェイスのサポートの使用を特定のシナリオをカスタマイズできます。 プロジェクト サブタイプの詳細については、次を参照してください。[プロジェクト サブタイプ](../../extensibility/internals/project-subtypes.md)します。  
  
## <a name="see-also"></a>関連項目  
 [Windows のドキュメントおよびエディター](http://msdn.microsoft.com/en-us/603625e1-62b6-413a-bc44-089346e166bc)   
 [チェックリスト: 新しいプロジェクトの種類を作成します。](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Visual Studio での階層](../../extensibility/internals/hierarchies-in-visual-studio.md)

