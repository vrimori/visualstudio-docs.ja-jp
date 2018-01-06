---
title: "プロジェクトの種類を作成する場合 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: project types, conditions for creating
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f766619054ed1912d677ac08fad511cfd3a3dcb4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="when-to-create-project-types"></a>プロジェクトの種類を作成する場合
カスタマイズするための基礎を提供新しいプロジェクトの種類を作成する[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ユーザー向けです。 ただし、新しいプロジェクトの種類を作成する必要はありませんすべて[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]カスタマイズします。 次のガイドラインには、新しいプロジェクトの種類が、シナリオに必要かどうかを判断するのに役立ちます。  
  
## <a name="create-a-new-project-type"></a>新しいプロジェクトの種類を作成します。  
 カスタマイズする場合は、プロジェクトの種類を作成する必要があります[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]次の方法の 1 つ以上で動作します。  
  
-   配置、構成、およびソース管理、ビルドに参加します。  
  
-   デバッグのサポートを提供します。  
  
-   プロジェクト項目を表示**ソリューション エクスプ ローラー**です。  
  
-   使用して、**プロジェクトを開く**または**新しいプロジェクト** ダイアログ ボックス。  
  
-   プロジェクトの入れ子をサポートします。  
  
## <a name="extend-an-existing-project-type"></a>既存のプロジェクトの種類を拡張します。  
 使用できる新しいプロジェクトの種類を作成する場合があります[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]変更または既存のプロジェクトの種類の動作を拡張する次の方法でのビルド プロセスを変更するなど、[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]プロジェクト。  
  
-   1 つの単位として複数のファイルを使用します。  
  
-   サブ項目の階層として 1 つのファイルを表示します。  
  
-   エディターの周囲コマンド コンテキストを表示します。  
  
-   エディターのサービス コンテキストを表示します。  
  
## <a name="use-an-existing-project-type"></a>既存のプロジェクトの種類を使用します。  
 新しいプロジェクトを作成する必要がありますされません。 次の表は、プロジェクトの種類を作成する必要がないタスクを示します。  
  
|タスク|説明|  
|----------|-----------------|  
|コマンドの処理|任意の VSPackage では、コマンドを処理できます。|  
|エディターの構築|カスタム エディターを登録することができます。 詳細については、次を参照してください。[ドキュメント ウィンドウおよびエディター](http://msdn.microsoft.com/en-us/603625e1-62b6-413a-bc44-089346e166bc)です。|  
|Windows を所有しています。|新しいプロジェクトの種類を追加することがなく、両方のツールとドキュメント ウィンドウを作成できます。|  
|[プロパティ] ウィンドウでプロパティを公開します。|すべてのオブジェクトには、プロパティを公開できます。|  
  
## <a name="create-a-project-subtype"></a>プロジェクトのサブタイプを作成します。  
 プロジェクトのサブタイプを使用すると、新しいプロジェクトの種類を作成するのにことがなく、マネージ プロジェクトの種類を拡張します。 プロジェクトのサブタイプでは、COM 集成を使用して、Microsoft で記述されたマネージ プロジェクトを拡張する[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]または[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]です。 COM 集成マネージ プロジェクト システムの実装の大部分を再利用でき、まだ集約とインターフェイスのサポートの使用から特定のシナリオ用にカスタマイズできます。 プロジェクトのサブタイプの詳細については、次を参照してください。[プロジェクト サブタイプ](../../extensibility/internals/project-subtypes.md)です。  
  
## <a name="see-also"></a>参照  
 [ドキュメント ウィンドウおよびエディター](http://msdn.microsoft.com/en-us/603625e1-62b6-413a-bc44-089346e166bc)   
 [チェックリスト: 新しいプロジェクトの種類を作成します。](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Visual Studio での階層](../../extensibility/internals/hierarchies-in-visual-studio.md)