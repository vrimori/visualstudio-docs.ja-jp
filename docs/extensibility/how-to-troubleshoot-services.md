---
title: '方法: サービスのトラブルシューティング |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, troubleshooting
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 77c168f2e47cbedd4e565dd3758389461ce148b6
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500395"
---
# <a name="how-to-troubleshoot-services"></a>方法: サービスのトラブルシューティング
これには、サービスを取得するときに発生する可能性があるいくつかの一般的な問題があります。  
  
-   サービスが登録されていない[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]します。  
  
-   インターフェイスの種類によって、サービスの種類ではなく、サービスを要求します。  
  
-   サービスを要求する VSPackage が配置されてされていません。  
  
-   間違ったサービス プロバイダーが使用されます。  
  
 かどうか、要求されたサービスを取得できない呼び出し<xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>は null を返します。 サービスを要求した後は、null の常にテストする必要があります。  
  
```csharp  
IVsActivityLog log =   
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
if (log == null) return;  
```  
  
## <a name="to-troubleshoot-a-service"></a>サービスをトラブルシューティングするには  
  
1.  システム レジストリにサービスが正しく登録されているかどうかを確認します。 詳細については、次を参照してください。[方法: サービスを提供](../extensibility/how-to-provide-a-service.md)します。  
  
     次 *.reg*ファイル フラグメントは、SVsTextManager サービスを登録する方法を示しています。  
  
    ```  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]  
    @="{F5E7E720-1401-11d1-883B-0000F87579D2}"  
    "Name"="SVsTextManager"  
    ```  
  
     上記の例では、バージョン番号は、バージョンの[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]12.0 または 14.0、キー {f5e7e71d-1401-11d1-883b-0000f87579d2} は、サービス、SVsTextManager および既定値の {のサービス識別子 (SID) など、F5E7E720-1401-11d1-883B-0000F87579D2} は、テキスト マネージャー サービスを提供する VSPackage のパッケージ GUID です。  
  
2.  GetService を呼び出すときに、サービスの種類と、インターフェイス型ではなくを使用します。 サービスを要求するときに[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、<xref:Microsoft.VisualStudio.Shell.Package>型から GUID を抽出します。 次の条件が存在しない場合、サービスは見つかりませんされます。  
  
    1.  インターフェイス型は、サービスの種類ではなく、GetService に渡されます。  
  
    2.  GUID は、インターフェイスを明示的に割り当てられません。 そのため、システムは、必要に応じてオブジェクトの既定の GUID を作成します。  
  
3.  サービスを要求する VSPackage が配置されていることを確認します。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 呼び出す前に、構築した後は、VSPackage をサイト<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>します。  
  
     サービスを必要がある VSPackage コンス トラクターでコードがあればに移動して、`Initialize`メソッド。  
  
4.  適切なサービス プロバイダーを使用していることを確認します。  
  
     すべてのサービス プロバイダーは同じです。 サービス プロバイダーを[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ツール ウィンドウへのパスと、VSPackage に渡す 1 つは異なります。 ツール ウィンドウのサービス プロバイダーが知って<xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>で認識されていないが、<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>します。 呼び出すことができます<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>ツール ウィンドウ内から VSPackage サービス プロバイダーを取得します。  
  
     ツール ウィンドウは、ユーザー コントロールまたはその他のすべてのコントロール コンテナーをホストしている場合、コンテナーが、Windows のコンポーネント モデルによって配置されている場合し、へのアクセスはありません。[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]サービス。 呼び出すことができます<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>コントロール コンテナー内から VSPackage サービス プロバイダーを取得します。  
  
## <a name="see-also"></a>関連項目  
 [利用可能なサービスの一覧](../extensibility/internals/list-of-available-services.md)   
 [使用し、サービスを提供](../extensibility/using-and-providing-services.md)   
 [サービスの基本情報](../extensibility/internals/service-essentials.md)