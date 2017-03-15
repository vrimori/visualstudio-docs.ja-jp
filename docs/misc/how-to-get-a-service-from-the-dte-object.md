---
title: "方法: DTE オブジェクトからサービスを取得する | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "サービス、DTE オブジェクトから"
ms.assetid: c26a51d4-86f0-454b-9625-5443e55eec7d
caps.latest.revision: 13
caps.handback.revision: 13
manager: "douge"
---
# 方法: DTE オブジェクトからサービスを取得する
サービスは [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のオートメーション <xref:EnvDTE.DTEClass> のオブジェクトにアクセスするすべてのプログラムから取得できます。  たとえば、ウィザードから DTE オブジェクトを通じて <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> サービスにアクセスできます。  アクティビティ ログに書き込むにこのサービスを使用できます。  詳細については、「[方法: 動作状況ログの使用](../extensibility/how-to-use-the-activity-log.md)」を参照してください。  
  
 DTE オブジェクトは、 <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>を使用して、マネージ コードでサービスを照会するために使用できる <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>を実装します。  
  
### サービスを DTE オブジェクトから取得するには  
  
1.  次のコードは、 DTE オブジェクトから <xref:Microsoft.VisualStudio.Shell.ServiceProvider> を作成し、 <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> サービスの種類がの <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> をダイヤルします。  サービスは、アクティビティ ログにエントリを作成するときに使用するインターフェイス <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>にキャストします。  詳細について abou に対してアクティビティ ログに書き込む方法 " を参照してください。 [方法: 動作状況ログの使用](../extensibility/how-to-use-the-activity-log.md)  
  
     [!code-cs[GetAServiceFromTheDTEObject#1](../misc/codesnippet/CSharp/how-to-get-a-service-from-the-dte-object_1.cs)]
     [!code-vb[GetAServiceFromTheDTEObject#1](../misc/codesnippet/VisualBasic/how-to-get-a-service-from-the-dte-object_1.vb)]  
  
## 参照  
 [使用して、サービスを提供します。](../extensibility/using-and-providing-services.md)   
 [サービスの基礎](../extensibility/internals/service-essentials.md)