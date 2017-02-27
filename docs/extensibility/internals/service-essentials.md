---
title: "サービスの基礎 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "essentials のサービス"
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# サービスの基礎
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

サービスは、2 つの VSPackages 間のコントラクトです。 1 つの VSPackage では、別の VSPackage を使用するためのインターフェイスの特定のセットを提供します。[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 自体は、サービスを提供するその他の VSPackages にある Vspackage のコレクションです。  
  
 たとえば、SVsActivityLog サービスを使用すると、アクティビティ ログへの書き込みに使用できる IVsActivityLog インターフェイスを取得します。 詳細については、「[方法: 動作状況ログの使用](../../extensibility/how-to-use-the-activity-log.md)」を参照してください。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 登録されていないいくつかの組み込みサービスを提供します。 VSPackages は、サービスの上書きを提供することによって組み込み、その他のサービスを置き換えることができます。 1 つのサービスの上書きがすべてのサービスに許可されます。  
  
 サービスの探索可能性があるありません。 したがってを消費する、適用するサービスのサービス識別子 \(SID\) を知る必要があり、それが提供するインターフェイスを知る必要があります。 サービスのリファレンス ドキュメントでは、この情報を提供します。  
  
-   Vspackages にあるサービスを提供するには、サービス プロバイダーが呼び出されます。  
  
-   その他の VSPackages に提供されているサービスは、グローバル サービスと呼ばれます。  
  
-   実装するには、VSPackage にのみ、または任意のオブジェクトを作成するかどうかを利用できるサービスは、ローカル サービスと呼ばれます。  
  
-   組み込みのサービスまたは他のパッケージで提供されるサービス交換サービスは、サービスの上書きと呼ばれます。  
  
-   サービス、またはサービスの上書きが要求時に読み込まれて、サービスを提供が別の VSPackage から要求された場合は、サービス プロバイダーが読み込まれます。  
  
-   サービス プロバイダーがそのグローバル サービスを登録、オンデマンドの読み込みをサポートするために [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。 詳細については、「[サービスの登録](../../misc/registering-services.md)」を参照してください。  
  
-   サービスを入手したらを使用して [QueryInterface](/visual-cpp/atl/queryinterface) \(アンマネージ コード\) またはキャスト \(マネージ コード\) などの目的のインターフェイスを取得します。  
  
    ```vb#  
    TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
    ```  
  
    ```c#  
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
  
    ```  
  
-   マネージ コードは、アンマネージ コードは、サービスをその GUID で、その型によって、サービスを参照します。  
  
-   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage を読み込む、サービス プロバイダーに渡す VSPackage へ VSPackage アクセス グローバル サービスを指定します。 これは、VSPackage を「配置」と呼ばれます。  
  
-   Vspackage では、作成したオブジェクトに対するサービス プロバイダーを指定できます。 たとえば、フォームに送信する色のサービスに対する要求のフレームには、これに要求を渡すことがあります [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。  
  
-   深く入れ子になったか、まったくが配置されていないマネージ オブジェクトを呼び出すことが <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> グローバル サービスに直接アクセスします。 詳細については、「[方法: GetGlobalService を使用する](../../misc/how-to-use-getglobalservice.md)」を参照してください。  
  
## 参照  
 [サービスの一覧](../../extensibility/internals/list-of-available-services.md)   
 [使用して、サービスを提供します。](../../extensibility/using-and-providing-services.md)   
 [キャストと型変換](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)   
 [キャスト](/visual-cpp/cpp/casting)