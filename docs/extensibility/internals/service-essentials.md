---
title: Essentials のサービス |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3428deeaf0e9cdc2aa926f5b1ff17b5030540f2b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53867278"
---
# <a name="service-essentials"></a>サービスの基本情報
サービスは、2 つの Vspackage の間のコントラクトです。 1 つの VSPackage では、別の VSPackage を使用するためのインターフェイスの特定のセットを提供します。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 自体は、その他の Vspackage にサービスを提供する Vspackage のコレクションです。  
  
 たとえば、SVsActivityLog サービスを使用すると、アクティビティ ログへの書き込みに使用できる、IVsActivityLog インターフェイスを取得します。 詳細については、「[方法 :アクティビティ ログを使用して、](../../extensibility/how-to-use-the-activity-log.md)します。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 登録されていないいくつかの組み込みサービスを提供します。 Vspackage では、サービスのオーバーライドを提供することで、組み込みやその他のサービスを置き換えることができます。 1 つのサービスのオーバーライドは、すべてのサービスに許可されます。  
  
 サービスには、見つけやすさはあるありません。 したがってを使用するサービスのサービス識別子 (SID) を知る必要がありますを提供するインターフェイスを知る必要があります。 サービスのリファレンス ドキュメントは、この情報を提供します。  
  
- サービスを提供する Vspackage は、サービス プロバイダーと呼ばれます。  
  
- その他の Vspackage に提供されるサービスは、グローバル サービスと呼ばれます。  
  
- または、それらを実装する VSPackage にのみ、任意のオブジェクトを作成するかどうかを利用できるサービスは、ローカル サービスと呼ばれます。  
  
- 組み込みのサービスまたは他のパッケージで提供されるサービスを置き換えるサービスは、サービスの上書きと呼ばれます。  
  
- サービス、またはサービスの上書きがオンデマンドで読み込まれる、別の VSPackage に提供するサービスを要求すると、サービス プロバイダーが読み込まれます。  
  
- サービス プロバイダーをオンデマンドの読み込みをサポートするには、グローバル サービスを登録します[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。 詳細については、「[方法 :サービスを提供](../../extensibility/how-to-provide-a-service.md)します。  
  
- サービスを取得した後を使用して、 [QueryInterface](/cpp/atl/queryinterface) (アンマネージ コード) やなどの目的のインターフェイスを取得するキャスト (マネージ コード)。  
  
  ```vb  
  TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
  ```  
  
  ```csharp  
  GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
  ```  
  
- マネージ コードは、アンマネージ コードは、GUID によって、サービスには、その型によって、サービスを指します。  
  
- ときに[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]VSPackage を読み込む、グローバル サービスを VSPackage のアクセスを提供する VSPackage に、サービス プロバイダーを渡されます。 これは、VSPackage を「配置」と呼ばれます。  
  
- Vspackage では、サービス プロバイダーを作成するオブジェクトを指定できます。 たとえば、フォームはへの要求を渡すことがあります、そのフレームに色サービスに対する要求を送信可能性があります[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。  
  
- 深く入れ子になったか、まったくが配置されていないマネージ オブジェクトを呼び出すことが<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>グローバル サービスに直接アクセスします。   
  
<a name="how-to-use-getglobalservice"></a>  
  
## <a name="use-getglobalservice"></a>GetGlobalService を使用します。  
  
場合によっては、ツール ウィンドウからサービスを取得するサービスを認識しませんが、サービス プロバイダーをコンテナーに配置されているか、またはしない配置されているコンテナーを制御したり必要があります。 たとえば、コントロール内からアクティビティ ログに書き込む可能性があります。 これらおよびその他のシナリオの詳細については、次を参照してください。[方法。サービスのトラブルシューティング](../../extensibility/how-to-troubleshoot-services.md)します。  
  
ほとんどの Visual Studio サービスを取得するには、静的で<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>メソッド。  
  
<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 依存パッケージから派生したすべての VSPackage を初めて初期化されるプロバイダーが配置されたキャッシュ サービスにします。 この条件が満たされるか、または null のサービスに対応することを保証する必要があります。  
  
さいわい、<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>ほとんどの場合、正常に動作します。  
  
-   VSPackage では、別の VSPackage にしか認識サービスを提供する場合、サービスを要求する VSPackage は、サービスが読み込まれるを提供する VSPackage の前に配置されてます。  
  
-   ツール ウィンドウを作成する場合は、VSPackage によっては、ツール ウィンドウを作成する前に、VSPackage が配置されました。  
  
-   VSPackage で作成したツール ウィンドウでコントロールのコンテナーがホストされている場合は、コントロールのコンテナーを作成する前に、VSPackage が配置されました。  
  
### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>ツール ウィンドウまたはコントロールのコンテナー内からサービスを取得するには  
  
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
    
    このコードは、SVsActivityLog サービスを取得し、アクティビティ ログへの書き込みに使用できる IVsActivityLog インターフェイスにキャストされます。 例については、次を参照してください。[方法。アクティビティ ログを使用して、](../../extensibility/how-to-use-the-activity-log.md)します。  
  
## <a name="see-also"></a>関連項目  
 [利用可能なサービスの一覧](../../extensibility/internals/list-of-available-services.md)   
 [使用して、サービスを提供します。](../../extensibility/using-and-providing-services.md)   
 [キャストと型変換](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)   
 [キャスト](/cpp/cpp/casting)