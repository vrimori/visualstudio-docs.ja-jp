---
title: "シンボルのプロバイダー | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "シンボル ハンドラー"
  - "[デバッグ SDK] シンボル ハンドラーのデバッグ"
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# シンボルのプロバイダー
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

式エバリュエーターでは変数や式を評価する言語コンパイラによって生成されるシンボリック デバッグ情報にアクセスする必要があります。  またシンボル ハンドラーと呼ばれる記号のプロバイダー \(SP\) インターフェイスの実装によってアクセスします。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] はプログラム データベースのシンボル ファイル形式を使用してマネージ コードとネイティブ コードの \(PDB\) SPS を指定します。  カスタム形式で保存されたシンボルを使用するプログラムの強い必要がある [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] によって提供される SPS を使用することをお勧めします。  
  
## 実装のメモ  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のデバッグ エンジンは共通言語ランタイムのインターフェイスを使用して SPS と通信 \(CLR\) することを想定しています。  その結果Visual Studio のデバッグ エンジンを使用して SP はCLR をサポートする必要があります。  すべての CLR のデバッグ インターフェイスの完全なリストを [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)] の一部である debugref.doc を参照してください。  
  
 SP がカスタムのデバッグ エンジンを使用するとデバッグ エンジンのニーズによって切り替えると必要に SP を実行できます。  
  
## 参照  
 [デバッガーのコンポーネント](../../extensibility/debugger/debugger-components.md)