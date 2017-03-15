---
title: "COM Interop unregistration failed | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.cannot_unregister_com2"
ms.assetid: 1172b560-c4b0-4aff-9f74-cf9b29ff76d9
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# COM Interop unregistration failed
古いアセンブリのコピーを登録するときに、問題が発生しました。  
  
 **\[COM の相互運用機能に登録\]** プロパティが設定されている場合、プロジェクト システムは、最初に古いコピーの COM オブジェクトを登録解除してから、ビルドされたコピーを登録します。  これは、レジストリを最新の状態に維持するために行われます。  
  
 **\[COM の相互運用機能に登録\]** プロパティにアクセスするには、\[構成プロパティ\] フォルダーの **\[ビルド\]** プロパティを参照してください。  
  
 エラーの原因として、次のことが考えられます。  
  
-   アセンブリの以前のタイプ ライブラリを登録解除できない。  レジストリのアクセス権が原因になっている可能性もあります。  
  
-   古いアセンブリを登録解除できない。  これは、レジストリのアクセス許可に問題がある可能性があります。  
  
 登録解除のプロセスが失敗すると、タイプ ライブラリの GUID の場合と同様に、CoCreatable オブジェクトの GUID のリークが発生します。  ただし、全体的なビルド プロセスは正常に行われます。  
  
## 参照  
 [COM Interoperability in .NET Framework Applications](/dotnet/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications)