---
title: "サービスの Essentials |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 8ff357d7ed3542a01cf8d98e36b9d0e99a122864
ms.lasthandoff: 04/05/2017

---
# <a name="service-essentials"></a>サービスの基礎
サービスは、次の 2 つの Vspackage の間のコントラクトです。 1 つの VSPackage では、別の VSPackage を使用するためのインターフェイスの特定のセットを提供します。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]自体は、その他の Vspackage にサービスを提供する Vspackage のコレクションです。  
  
 たとえば、SVsActivityLog サービスを使用すると、アクティビティ ログへの書き込みに使用できる、IVsActivityLog インターフェイスを取得します。 詳細については、次を参照してください。[する方法: アクティビティ ログを使用して](../../extensibility/how-to-use-the-activity-log.md)です。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]登録されていないいくつかの組み込みサービスも用意されています。 Vspackage では、サービス オーバーライドを提供することにより、組み込みまたはその他のサービスを置き換えることができます。 任意のサービスには、1 つのサービスの上書きが許可します。  
  
 サービス探索可能性があるありません。 したがってを使用するサービスのサービス識別子 (SID) を知る必要があります、提供するインターフェイスを知る必要があります。 サービスに関するリファレンス ドキュメントは、この情報を提供します。  
  
-   サービスを提供する Vspackage は、サービス プロバイダーと呼ばれます。  
  
-   その他の Vspackage に提供されているサービスは、グローバル サービスと呼ばれます。  
  
-   または、それらを実装する VSPackage にのみ、任意のオブジェクトを作成するかどうかを利用できるサービスは、ローカル サービスと呼ばれます。  
  
-   組み込みのサービスまたは他のパッケージで提供されるサービスを置き換えるサービスは、サービスの上書きと呼ばれます。  
  
-   サービス、またはサービス オーバーライドが要求時に読み込まれて、別の VSPackage によって提供するサービスが要求されたときに、サービス プロバイダーが読み込まれます。  
  
-   オンデマンド読み込みをサポートするために、サービス プロバイダーとグローバル サービスを登録[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。 詳細については、次を参照してください。[サービスの登録](../../misc/registering-services.md)です。  
  
-   サービスを取得した後を使用して[QueryInterface](/cpp/atl/queryinterface) (アンマネージ コード) またはなどの目的のインターフェイスを取得するキャスト (マネージ コード)。  
  
    ```vb#  
    TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
    ```  
  
    ```c#  
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
  
    ```  
  
-   マネージ コードは、アンマネージ コードは、GUID によって、サービス、その型によって、サービスを参照します。  
  
-   ときに[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]VSPackage を読み込む、サービス プロバイダーに渡して、VSPackage にグローバル サービスを VSPackage のアクセスを付与します。 これは、VSPackage を"サイト"設定と呼ばれます。  
  
-   Vspackage では、作成したオブジェクトに対するサービス プロバイダーを指定できます。 たとえば、フォームは、そのフレームは、要求を渡すことがありますのカラー サービスの要求を送信可能性があります[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。  
  
-   深く入れ子になっているか、まったくが配置されていない管理対象のオブジェクトを呼び出すことが<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>グローバル サービスに直接アクセスする</xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>。 詳細については、次を参照してください。[する方法: 使用 GetGlobalService](../../misc/how-to-use-getglobalservice.md)です。  
  
## <a name="see-also"></a>関連項目  
 [使用可能なサービスの一覧](../../extensibility/internals/list-of-available-services.md)   
 [使用して、サービスを提供します。](../../extensibility/using-and-providing-services.md)   
 [キャストと型変換](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)   
 [キャスト](/cpp/cpp/casting)
