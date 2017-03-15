---
title: "デバッグ エンジンの実装方法を選択します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "デバッグ エンジンは、実装戦略"
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# デバッグ エンジンの実装方法を選択します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

デバッグ エンジンの実装方法を決定するためにランタイム アーキテクチャを \(DE\) 使用します。  デバッグ エンジンはVisual Studio セッションのデバッグ マネージャー \(SDM\) にINPROCまたは両方の手順でデバッグするプログラムを作成したインプロセスである場合があります。  次のガイドラインではこの 3 種類の方法で選択してください。  
  
## ガイドライン  
 DE SDM をデバッグするとプログラムの両方への手順であることはできませんが通常必要はありません。  プロセスの境界を越えた呼び出しは比較的があります。  
  
 デバッグ エンジンはWin32 ネイティブ ランタイム環境に共通言語ランタイム環境によって提供されます。  これらの環境のいずれかの de\-DE を置き換える必要がある場合はSDM の de\-DE in\-process を作成する必要があります。  
  
 はSDM にします in\-process デバッグするプログラムに作成するかを選択できます。  シンボル ストアで迅速にアクセスするためのメモリに読み込むことができるかどうかを考慮することが重要かどうかをプログラムのシンボル ストアにします needs を頻繁にアクセスする式エバリュエーターおよびです。  また次の点を考慮する :  
  
-   式エバリュエーターとシンボル ストアの間に多くの呼び出しがない場合またはシンボル ストアで SDM のメモリ空間に読み込むことができる SDM にします in\-process を作成します。  プログラムにアタッチすると SDM にデバッグ エンジンの CLSID を返す必要があります。  SDM は de\-DE の INPROC のインスタンスを作成するにはこの CLSID を使用します。  
  
-   シンボル ストアにアクセスできるようにしますがプログラムを呼び出す必要がある場合はプログラムで de\-DE in\-process を作成します。  この場合プログラムは de\-DE のインスタンスを作成します。  
  
## 参照  
 [Visual Studio デバッガーの拡張性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)