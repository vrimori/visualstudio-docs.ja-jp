---
title: Essentials のサービス |Microsoft Docs
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
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 497f894f1ae8eef6c58ffeea542128105a51336b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47546447"
---
# <a name="service-essentials"></a>サービスの基本情報
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[Service Essentials](https://docs.microsoft.com/visualstudio/extensibility/internals/service-essentials)します。  
  
サービスは、2 つの Vspackage の間のコントラクトです。 1 つの VSPackage では、別の VSPackage を使用するためのインターフェイスの特定のセットを提供します。 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 自体は、その他の Vspackage にサービスを提供する Vspackage のコレクションです。  
  
 たとえば、SVsActivityLog サービスを使用すると、アクティビティ ログへの書き込みに使用できる、IVsActivityLog インターフェイスを取得します。 詳細については、次を参照してください。[方法: アクティビティ ログを使用して、](../../extensibility/how-to-use-the-activity-log.md)します。  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 登録されていないいくつかの組み込みサービスを提供します。 Vspackage では、サービスのオーバーライドを提供することで、組み込みやその他のサービスを置き換えることができます。 1 つのサービスのオーバーライドは、すべてのサービスに許可されます。  
  
 サービスには、見つけやすさはあるありません。 したがってを使用するサービスのサービス識別子 (SID) を知る必要がありますを提供するインターフェイスを知る必要があります。 サービスのリファレンス ドキュメントは、この情報を提供します。  
  
-   サービスを提供する Vspackage は、サービス プロバイダーと呼ばれます。  
  
-   その他の Vspackage に提供されるサービスは、グローバル サービスと呼ばれます。  
  
-   または、それらを実装する VSPackage にのみ、任意のオブジェクトを作成するかどうかを利用できるサービスは、ローカル サービスと呼ばれます。  
  
-   組み込みのサービスまたは他のパッケージで提供されるサービスを置き換えるサービスは、サービスの上書きと呼ばれます。  
  
-   サービス、またはサービスの上書きがオンデマンドで読み込まれる、別の VSPackage に提供するサービスを要求すると、サービス プロバイダーが読み込まれます。  
  
-   サービス プロバイダーをオンデマンドの読み込みをサポートするには、グローバル サービスを登録します[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]します。 詳細については、次を参照してください。[サービス登録](../../misc/registering-services.md)します。  
  
-   サービスを取得した後を使用して、 [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) (アンマネージ コード) やなどの目的のインターフェイスを取得するキャスト (マネージ コード)。  
  
    ```vb  
    TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
    ```  
  
    ```csharp  
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
  
    ```  
  
-   マネージ コードは、アンマネージ コードは、GUID によって、サービスには、その型によって、サービスを指します。  
  
-   ときに[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]VSPackage を読み込む、グローバル サービスを VSPackage のアクセスを提供する VSPackage に、サービス プロバイダーを渡されます。 これは、VSPackage を「配置」と呼ばれます。  
  
-   Vspackage では、サービス プロバイダーを作成するオブジェクトを指定できます。 たとえば、フォームはへの要求を渡すことがあります、そのフレームに色サービスに対する要求を送信可能性があります[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]します。  
  
-   深く入れ子になったか、まったくが配置されていないマネージ オブジェクトを呼び出すことが<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>グローバル サービスに直接アクセスします。 詳細については、次を参照してください。[方法: GetGlobalService を使用して](../../misc/how-to-use-getglobalservice.md)します。  
  
## <a name="see-also"></a>関連項目  
 [利用可能なサービスの一覧](../../extensibility/internals/list-of-available-services.md)   
 [使用して、サービスを提供します。](../../extensibility/using-and-providing-services.md)   
 [キャストと型変換](http://msdn.microsoft.com/library/568df58a-d292-4b55-93ba-601578722878)   
 [キャスト](http://msdn.microsoft.com/library/3dbeb06e-2f4b-4693-832d-624bc8ec95de)

