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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 0b78b5f9bf1fb6d9c92657b99e6d21b58cab2728
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

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
  
-   オンデマンド読み込みをサポートするために、サービス プロバイダーとグローバル サービスを登録[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。 詳細については、次を参照してください。[する方法: サービスを提供](../../extensibility/how-to-provide-a-service.md)です。  
  
-   サービスを取得した後を使用して[QueryInterface](/cpp/atl/queryinterface) (アンマネージ コード) またはなどの目的のインターフェイスを取得するキャスト (マネージ コード)。  
  
    ```vb  
    TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
    ```  
  
    ```csharp  
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    ```  
  
-   マネージ コードは、アンマネージ コードは、GUID によって、サービス、その型によって、サービスを参照します。  
  
-   ときに[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]VSPackage を読み込む、サービス プロバイダーに渡して、VSPackage にグローバル サービスを VSPackage のアクセスを付与します。 これは、VSPackage を"サイト"設定と呼ばれます。  
  
-   Vspackage では、作成したオブジェクトに対するサービス プロバイダーを指定できます。 たとえば、フォームは、そのフレームは、要求を渡すことがありますのカラー サービスの要求を送信可能性があります[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。  
  
-   深く入れ子になっているか、まったくが配置されていない管理対象のオブジェクトを呼び出すことが<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>グローバル サービスに直接アクセスします。   
  
<a name="how-to-use-getglobalservice"></a>  
  
## <a name="use-getglobalservice"></a>GetGlobalService を使用します。  
  
ツール ウィンドウからサービスを取得またはサービスが認識していないサービス プロバイダーのコンテナーに配置されているか、または配置されていないするコンテナーを制御する必要があります。 たとえば、コントロール内のアクティビティ ログに書き込むことができます。 これらおよびその他のシナリオの詳細については、次を参照してください。[する方法: サービスのトラブルシューティングを行う](../../extensibility/how-to-troubleshoot-services.md)です。  
  
ほとんどの Visual Studio サービスを取得するには、静的なを呼び出すことによって<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>メソッドです。  
  
<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>依存しているキャッシュされたサービスに初めてパッケージから派生した任意の VSPackage が初期化されているプロバイダーが配置されています。 この条件を満たすには、か、または null のサービスの準備をするを保証する必要があります。  
  
さいわい、<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>ほとんどの時間が正常に動作します。  
  
-   VSPackage では、別の VSPackage にしか認識サービスを提供する場合、サービスを要求する VSPackage は、サービスが読み込まれるを提供する VSPackage の前に配置されてます。  
  
-   VSPackage でツール ウィンドウを作成する場合は、ツール ウィンドウを作成する前に、VSPackage が配置されました。  
  
-   コントロールのコンテナーが VSPackage によって作成されたツール ウィンドウでホストされている場合は、コントロールのコンテナーが作成される前に、VSPackage が配置されました。  
  
### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>ツール ウィンドウまたはコントロールのコンテナー内からのサービスを取得するには  
  
-   このコードをコンス トラクター、ツール ウィンドウ、またはコントロールのコンテナーに挿入します。  
  
    ```csharp  
    IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;
        if (log == null) return;
    ```  
    ```vb  
    Dim log As IVsActivityLog = TryCast(Package.GetGlobalService(GetType(SVsActivityLog)), IVsActivityLog)
    If log Is Nothing Then
        Return
    End If
    ```  
    
    このコードは、SVsActivityLog サービスを取得し、アクティビティ ログへの書き込みに使用できる IVsActivityLog インターフェイスにキャストします。 例については、次を参照してください。[する方法: アクティビティ ログを使用して](../../extensibility/how-to-use-the-activity-log.md)です。  
  
## <a name="see-also"></a>関連項目  
 [使用可能なサービスの一覧](../../extensibility/internals/list-of-available-services.md)   
 [使用して、サービスを提供します。](../../extensibility/using-and-providing-services.md)   
 [キャストと型変換](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)   
 [キャスト](/cpp/cpp/casting)
