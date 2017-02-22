---
title: "型のビジュアライザーとカスタム ビューアー | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "[デバッグ SDK] カスタム ビューアーのデバッグ"
  - "[デバッグ SDK] 型のビジュアライザーのデバッグ"
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# 型のビジュアライザーとカスタム ビューアー
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

型のビジュアライザーはきわめて特殊な形式の任意のデータを表示するコンポーネントです。  この形式はビジュアライザーのエンド ユーザーやサードパーティのサプライヤーに応じてビジュアライザーの実装によって完全にあります。  
  
 カスタム ビューアーは特定の形式の任意のデータを表示するカスタムの式エバリュエーターの一部です。  この形式はカスタム ビューアーの実装によって完全にあるため形式の式エバリュエーターの実装によってあることを意味 \(EE\) します。  
  
## 式エバリュエーター型のビジュアライザーのサポート  
 EE はビジュアライザーにアクセスできる一連のインターフェイスをサポートしてビジュアライザーをサポートする型 : [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) と [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) などのインターフェイス。  EEが型のビジュアライザー自体の実装を担当していないので注意してください : EE は型情報に外部ビジュアライザーのアクセスを許可します。  このようなビジュアライザーは EE とともに出荷されそのほかのサードパーティ販売元によってもエンド ユーザーが指定する Visual Studio の適切な場所にインストールされる場合もあります。  
  
## 式エバリュエーターのカスタム ビューアーのサポート  
 EE はEE 自体がデータ型をレンダリングするためのコードを記述するカスタム ビューアーをサポートできます。  カスタム ビューアーは形式を有効にするデータを表示するのすべての関税を処理 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) のインターフェイスを実装しています ; ビューアーが表示されを完全に管理しデータの変更を許可できます。  製品に付属すると EE を指定するカスタム ビューアーが EE があります。  
  
## 参照  
 [デバッガーのコンポーネント](../../extensibility/debugger/debugger-components.md)   
 [式エバリュエーター](../../extensibility/debugger/expression-evaluator.md)   
 [エンジンをデバッグします。](../../extensibility/debugger/debug-engine.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)