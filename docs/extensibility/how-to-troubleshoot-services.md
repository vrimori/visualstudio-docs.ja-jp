---
title: "方法: サービスのトラブルシューティング | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "サービスのトラブルシューティング"
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# 方法: サービスのトラブルシューティング
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

サービスを取得しようとするときに発生する可能性があるいくつかの一般的な問題があります。  
  
-   サービスは登録されていない [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]します。  
  
-   インターフェイスの種類によって、サービスの種類ではなく、サービスが要求されます。  
  
-   サービスを要求する VSPackage が配置されているされません。  
  
-   正しくないサービス プロバイダーを使用するとします。  
  
 かどうか、要求したサービスを取得できないへの呼び出し <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> は null を返します。 サービスを要求した後は、null を常にテストする必要があります。  
  
```c#  
IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog; if (log == null) return;  
```  
  
### サービスをトラブルシューティングするには  
  
1.  サービスが正しく登録されているかどうかを調べるためにシステム レジストリを確認します。 詳細については、「[サービスの登録](../misc/registering-services.md)」を参照してください。  
  
     次の .reg ファイル フラグメントは、SVsTextManager サービスを登録する方法を示しています。  
  
    ```  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}] @="{F5E7E720-1401-11d1-883B-0000F87579D2}" "Name"="SVsTextManager"  
    ```  
  
     上記の例では、バージョン番号は、バージョンの [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], 、12.0 14.0 などキー {F5E7E71D\-1401\-11d1\-883B\-0000F87579D2} SVsTextManager、サービスのサービス識別子 \(SID\) は、既定値 {F5E7E720\-1401\-11d1\-883B\-0000F87579D2} パッケージ テキスト マネージャーは、サービスを提供する VSPackage の GUID。  
  
2.  GetService を呼び出す場合は、インターフェイス型ではなくおよびサービスの種類を使用します。 サービスを要求するときに [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], 、<xref:Microsoft.VisualStudio.Shell.Package> 型から GUID を抽出します。 次の条件に当てはまる場合、サービスを見つけることはできません。  
  
    1.  インターフェイス型は、サービス型ではなく、GetService に渡されます。  
  
    2.  インターフェイスに明示的に割り当てられている GUID はありません。 そのため、システムでは、必要に応じてオブジェクトの既定の GUID を作成します。  
  
3.  サービスを要求する VSPackage が配置されていることを確認します。[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] これを構築した後、呼び出しの前に、VSPackage をサイト <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>します。  
  
     サービスの必要のある VSPackage コンス トラクターでコードがある場合は、Initialize メソッドに移動します。  
  
4.  正しいサービス プロバイダーを使用していることを確認します。  
  
     すべてのサービス プロバイダーとは限りません。 サービス プロバイダーを [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSPackage に渡すものとは異なるツール ウィンドウに渡されます。 ツール ウィンドウ サービス プロバイダーが知って <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>, 、把握していませんが、 <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>です。 呼び出すことができます <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> ツール ウィンドウ内から VSPackage サービス プロバイダーを取得します。  
  
     ツール ウィンドウは、ユーザー コントロールまたはその他のコントロールのコンテナーをホストしている場合、コンテナーが Windows コンポーネントのモデルが配置されている場合し、いずれかにアクセス権がない [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] サービスです。 呼び出すことができます <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> をコントロール コンテナーの中である VSPackage サービス プロバイダーを取得します。  
  
## 参照  
 [サービスの一覧](../extensibility/internals/list-of-available-services.md)   
 [使用して、サービスを提供します。](../extensibility/using-and-providing-services.md)   
 [サービスの基礎](../extensibility/internals/service-essentials.md)