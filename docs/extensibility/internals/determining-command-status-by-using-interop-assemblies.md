---
title: "相互運用機能アセンブリを使用してコマンドのステータスの特定 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "コマンドのステータスの特定の相互運用機能アセンブリ"
  - "コマンド処理の状態の相互運用機能アセンブリ"
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# 相互運用機能アセンブリを使用してコマンドのステータスの特定
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

VSPackage 必要がありますの追跡を処理できるコマンドの状態。 環境は、VSPackage 内で処理コマンドが有効になっているしたり無効にした場合を判断できません。 コマンドの処理状態の環境に通知する、VSPackage の責任は、たとえば、一般の状態などのコマンド **切り取り**, 、**コピー**, 、および **貼り付け**します。  
  
## 状態通知のソース  
 環境が VSPackages' を通じてコマンドに関する情報を受け取る <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> VSPackage の実装の一部であるメソッドの <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> インターフェイスです。 環境の呼び出し、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> の 2 つの条件の下にある VSPackage メソッド。  
  
-   環境が実行される、ユーザーを右クリックして\) のメイン メニューまたはコンテキスト メニューが開いたら、 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> の状態を確認するには、そのメニューのコマンドのすべてのメソッドです。  
  
-   要求したときに VSPackage 環境が現在のユーザー インターフェイス \(UI\) を更新します。 などで、ユーザーに現在表示されているコマンドとこれが発生した、 **切り取り**, 、**コピー**, 、および **貼り付け** \[標準\] ツールバーをグループ化に有効にし、コンテキストとユーザーの操作への応答で無効にします。  
  
 シェルでは、複数の VSPackages をホストするため、シェルのパフォーマンスは許容範囲を超えるが低下する場合は、コマンドの状態を判断するには、各 VSPackage をポーリングする必要があります。 代わりに、変更時に、UI が変更されたときに、VSPackage は、環境を通知アクティブにする必要があります。 更新の通知の詳細については、次を参照してください。 [ユーザー インターフェイスの更新](../../extensibility/updating-the-user-interface.md)します。  
  
## 通知の状態エラー  
 コマンドの状態変更の環境に通知する、VSPackage の障害は、不整合な状態で、UI を配置できます。 メニューまたはコンテキスト メニュー コマンドのいずれかのことができますに配置することはツールバーに、ユーザーが覚えておいてください。 そのため、メニューまたはコンテキスト メニューを開いたときにのみ、UI の更新は不十分です。  
  
## 参照  
 [Vspackage でのユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [実装](../../extensibility/internals/command-implementation.md)