---
title: "例外のトラブルシューティング : System.Security.SecurityException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EHSecurity"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "System.Security.SecurityException クラス"
  - "SecurityException クラス"
ms.assetid: 7679ef74-dd15-439f-bfeb-0fb45f8b2373
caps.latest.revision: 26
caps.handback.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 例外のトラブルシューティング : System.Security.SecurityException
<xref:System.Security.SecurityException> 例外は、セキュリティ エラーが検出されるとスローされます。  
  
## 関連するヒント  
 プロパティ ページでアセンブリのアクセス許可レベルを調整します。  
 詳細については、「<xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.SqlPermissionLevel%2A>」を参照してください。  
  
 分離ストレージにアプリケーション データを格納します。  
 分離ストレージは、コードを保存データに関連付けるための標準的な方法を定義することによって、データの分離と安全を提供するデータ ストレージです。 詳細については、「[分離ストレージ](../Topic/Isolated%20Storage.md)」を参照してください。  
  
 <xref:System.Windows.Forms.OpenFileDialog> を使用するときは、<xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> メソッドを使用してファイルを開くか、保存します。  
 これにより、アプリケーションは部分的に信頼されている状況で動作します。  
  
 アプリケーションが、ローカル コンピューター上の既存のイベント ログに対して読み取りおよび書き込みを行っていることを確認します。  
 ローカル コンピューター以外のコンピューターに対してログオンの作成または書き込みを行うための十分なアクセス許可がアプリケーションに与えられていないことがあります。  
  
 アンマネージ ライブラリを呼び出すときは、同等のマネージ ライブラリを使用します。  
 同等の API がフレームワーク内に存在する場合があります。 詳細については、「[Troubleshooting Interoperability](/dotnet/visual-basic/programming-guide/com-interop/troubleshooting-interoperability)」を参照してください。  
  
 安全なウィンドウを使用します。  
 <xref:System.Security.Permissions.UIPermissionWindow> 列挙型は、コードが使用できるウィンドウの種類を指定します。  
  
 <xref:System.Windows.Forms.PrintDialog> コンポーネントを介した印刷をユーザーに許可します。  
 これにより、アプリケーションは部分的に信頼されている状況で動作します。 詳細については、「<xref:System.Windows.Forms.PrintDialog>」を参照してください。  
  
 既定のプリンターに印刷します。  
 これにより、アプリケーションは部分的に信頼されている状況で動作します。 権限を持たないプリンターにアクセスしようとしている可能性があります。  
  
 配置元と同じ Web サーバーからデータを取得します。  
 これにより、アプリケーションは部分的に信頼されている状況で動作します。  
  
 Office ソリューションを配置するときは、必要なすべてのセキュリティ要件を満たしていることを確認します。  
 詳細については、「[Office ソリューションに固有のセキュリティに関する考慮事項](/office-dev/office-dev/specific-security-considerations-for-office-solutions)」を参照してください。  
  
 カスタム セキュリティ オブジェクトを実装するアセンブリが他のアセンブリを参照する場合、参照されたアセンブリを完全信頼のアセンブリ リストに追加します。  
 詳細については、「[Caspol.exe \(コード アクセス セキュリティ ポリシー ツール\)](../Topic/Caspol.exe%20\(Code%20Access%20Security%20Policy%20Tool\).md)」を参照してください。  
  
## 参照  
 <xref:System.Security.SecurityException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)