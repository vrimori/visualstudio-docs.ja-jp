---
title: "COM Interop registration failed | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cannot_register_com2"
ms.assetid: d1b81f8e-66d7-4cfc-96ff-f1436a8f854a
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# COM Interop registration failed
COM クライアントに機能を公開するアセンブリの登録が失敗しました。  このエラーが発生した場合、ビルド プロセスは失敗します。  
  
 アセンブリは、COM クライアントに対してオブジェクトを公開できます。  プロジェクト システムには、Visual Basic 6 やスクリプト言語のクラスを使用できるようにタイプ ライブラリを生成したり登録したりするプロパティのほか、COM 相互運用機能の公開されたクラスを登録するプロパティも用意されています。  
  
 **\[COM の相互運用機能に登録\]** プロパティにアクセスするには、**\[構成プロパティ\]** フォルダーの **\[ビルド\]** プロパティ ページを参照してください。  
  
 エラーの原因として、次のことが考えられます。  
  
-   アセンブリのタイプ ライブラリが生成できない。  これは、ディスク容量の問題であるか、Visual Studio またはほかのプロセスによってタイプ ライブラリがロックされるファイル ロックの問題である可能性があります。  または、参照されたアセンブリのタイプ ライブラリが、システム上で正しく登録されなかった可能性もあります。  
  
-   生成されたタイプ ライブラリを登録できない。  レジストリのアクセス権が原因になっている可能性もあります。  
  
-   アセンブリにクラスを登録できない。  レジストリのアクセス権が原因になっている可能性もあります。  
  
 **このエラーを解決するには**  
  
-   コンピューター上のディスクの空き容量を増やします。  
  
-   ファイル ロックの問題がある場合は、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] を再起動します。  
  
-   管理者またはレジストリへのアクセス許可を持つグループのメンバーとしてログオンしてください。  
  
## 参照  
 [COM Interoperability in .NET Framework Applications](/dotnet/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications)