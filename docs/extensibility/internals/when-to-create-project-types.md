---
title: プロジェクトの種類を作成する場合 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, conditions for creating
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a8f759e24671bd397fba691a45f2b0417521064d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55023737"
---
# <a name="when-to-create-project-types"></a>プロジェクト タイプを作成する状況
カスタマイズするため、単位を提供する新しいプロジェクトの種類を作成する[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ユーザー向けです。 ただし、新しいプロジェクトの種類を作成する必要はありませんすべての[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]カスタマイズします。 次のガイドラインを使用するとは新しいプロジェクトの種類が、シナリオに必要かどうかを判断できます。  
  
## <a name="create-a-new-project-type"></a>新しいプロジェクトの種類を作成します。  
 カスタマイズする場合は、プロジェクトの種類を作成する必要があります[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]の次の方法の 1 つ以上を実行します。  
  
-   ビルドに参加、デプロイ、構成、およびソース管理。  
  
-   デバッグのサポートを提供します。  
  
-   プロジェクト アイテムの表示**ソリューション エクスプ ローラー**します。  
  
-   使用して、**プロジェクトを開く**または**新しいプロジェクト** ダイアログ ボックス。  
  
-   プロジェクトの入れ子をサポートします。  
  
## <a name="extend-an-existing-project-type"></a>既存のプロジェクトの種類を拡張します。  
 使用できる新しいプロジェクトの種類を作成したい場合があります[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]変更または既存のプロジェクトの種類の動作を拡張する次の方法でのビルド プロセスを変更するなど、[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]プロジェクト。  
  
-   1 つの単位として複数のファイルを使用します。  
  
-   サブ項目の階層として 1 つのファイルを表示します。  
  
-   エディターの周囲のコマンドのコンテキストを表示します。  
  
-   エディターに対し、サービス コンテキストを表示します。  
  
## <a name="use-an-existing-project-type"></a>既存のプロジェクトの種類を使用して、  
 新しいプロジェクトを作成する必要がありますされません。 次の表では、プロジェクトの種類を作成する必要はありませんが、タスクを示します。  
  
|タスク|説明|  
|----------|-----------------|  
|コマンドの処理|すべての VSPackage では、コマンドを処理できます。|  
|エディターの構築|カスタム エディターを登録することができます。 詳細については、次を参照してください。[ドキュメント Windows およびエディター](https://msdn.microsoft.com/library/603625e1-62b6-413a-bc44-089346e166bc)します。|  
|Windows を所有しています。|新しいプロジェクトの種類を追加せず、両方のツールとドキュメント ウィンドウを作成できます。|  
|[プロパティ] ウィンドウでプロパティを公開します。|すべてのオブジェクトには、プロパティを公開できます。|  
  
## <a name="create-a-project-subtype"></a>プロジェクト サブタイプを作成します。  
 プロジェクト サブタイプを使用して、新しいプロジェクトの種類を作成することがなく、マネージ プロジェクトの種類を拡張することができます。 プロジェクト サブタイプでは、COM の集計を使用して、Microsoft で記述されたマネージ プロジェクトを拡張する[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]または[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]します。 COM の集計を含むマネージ プロジェクト システムの実装の大部分を再利用し、集計と、インターフェイスのサポートの使用を特定のシナリオをカスタマイズできます。 プロジェクト サブタイプの詳細については、次を参照してください。[プロジェクト サブタイプ](../../extensibility/internals/project-subtypes.md)します。  
  
## <a name="see-also"></a>関連項目  
 [Windows のドキュメントおよびエディター](https://msdn.microsoft.com/library/603625e1-62b6-413a-bc44-089346e166bc)   
 [チェックリスト:新しいプロジェクトの種類を作成します。](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Visual Studio での階層](../../extensibility/internals/hierarchies-in-visual-studio.md)