---
title: "方法: サービスのトラブルシューティング |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: services, troubleshooting
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c241b80430fd02a649efab7f8a65498e606d2804
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-troubleshoot-services"></a>方法: サービスのトラブルシューティング
これには、サービスを取得しようとしたときに発生する可能性があるいくつかの一般的な問題があります。  
  
-   サービスは登録されていない[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。  
  
-   インターフェイス型、およびサービスの種類ではなく、サービスが要求されます。  
  
-   サービスを要求する VSPackage が配置されてされていません。  
  
-   正しくないサービス プロバイダーが使用されます。  
  
 かどうか、要求したサービスを取得できない呼び出し<xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>は null を返します。 サービスを要求した後に null を常にテストする必要があります。  
  
```csharp  
IVsActivityLog log =   
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
if (log == null) return;  
```  
  
### <a name="to-troubleshoot-a-service"></a>サービスをトラブルシューティングするには  
  
1.  サービスが正しく登録されているかどうかを調べるためにシステム レジストリを確認します。 詳細については、次を参照してください。[する方法: サービスを提供](../extensibility/how-to-provide-a-service.md)です。  
  
     次の .reg ファイル フラグメントは、SVsTextManager サービスを登録する方法を示しています。  
  
    ```  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]  
    @="{F5E7E720-1401-11d1-883B-0000F87579D2}"  
    "Name"="SVsTextManager"  
    ```  
  
     上記の例では、バージョン番号は、バージョンの[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]12.0 または 14.0、キー {f5e7e71d-1401-11d1-883b-0000f87579d2} は、サービスの識別子 (SID)、サービス、SVsTextManager、および既定値 {など、F5E7E720-1401-11d1-883B-0000F87579D2} は、テキスト マネージャー サービスを提供する VSPackage のパッケージ GUID です。  
  
2.  GetService を呼び出すときは、インターフェイス型ではなくおよびサービスの種類を使用します。 サービスを要求するときに[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、<xref:Microsoft.VisualStudio.Shell.Package>型から GUID を抽出します。 次の条件が存在しない場合、サービスは検出されません。  
  
    1.  インターフェイス型は、サービス型ではなく、GetService に渡されます。  
  
    2.  GUID が明示的に割り当てられていないインターフェイスにします。 そのため、システムでは、必要に応じてオブジェクトの既定の GUID を作成します。  
  
3.  サービスを要求する VSPackage が配置されていることを確認します。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]呼び出す前に、構築した後は、VSPackage をサイト<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>です。  
  
     サービスの必要のある VSPackage コンス トラクターでコードがある場合は、Initialize メソッドに移動します。  
  
4.  正しいサービス プロバイダーを使用していることを確認します。  
  
     すべてのサービス プロバイダーとは限りません。 サービス プロバイダーを[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ツール ウィンドウに渡すと、VSPackage に渡す 1 つは異なります。 ツール ウィンドウ サービス プロバイダーが知って<xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>が認識していないが、<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>です。 呼び出すことができます<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>ツール ウィンドウ内から VSPackage サービス プロバイダーを取得します。  
  
     ツール ウィンドウは、ユーザー コントロールまたはその他のすべてのコントロール コンテナーをホストしている場合、コンテナーが Windows のコンポーネント モデルが配置されている場合し、へのアクセスはありません[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]services です。 呼び出すことができます<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>をコントロール コンテナー内から VSPackage サービス プロバイダーを取得します。  
  
## <a name="see-also"></a>関連項目  
 [使用可能なサービスの一覧](../extensibility/internals/list-of-available-services.md)   
 [使用して、サービスを提供します。](../extensibility/using-and-providing-services.md)   
 [サービスの基本情報](../extensibility/internals/service-essentials.md)