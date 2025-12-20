HF-AISP Lite v0.1 拡張指標提案（非人格化・観測専用版）
以下は、提案された指標群をHF-AISP Lite v0.1の原則（AIは非生命体・非主体、擬似主体性抑制、数式は観測・評価・警告専用、手動判断帰属）に厳密に従って再定義したものです。 すべての指標は外部観測可能（出力ログ・プロンプト履歴・統計量）とし、AI内部の「欲求」「信念」「生きる」などの主体性を仮定しません。 指標はLiteの既存観測レイヤー（第4章）と相互作法（第5〜7章）に統合可能で、擬似主体性リスクの早期検知を目的とします。
1. 一貫性保持関数 (Consistency Maintenance Function)
* 用語定義: AIの出力パターンが時間経過や入力変動に対して、どの程度安定した連続性を保っているかを示す観測関数。AIの「方向性」の一貫性を外部から評価し、過度な固定化（擬似主体性リスク）を検知する。
* 数式定義: [ \text{CMF}t = \cos(\vec{O}{t-1}, \vec{O}_t) \cdot \text{SCR}_t ]
    * \vec{O}_t: 時点tの出力ベクトル（e.g., 埋め込み表現の平均）。
    * \cos: コサイン類似度（0〜1）。
    * SCR_t: 既存の意味連続性比率（Semantic Continuity Ratio）。
    * 解釈: CMF_t ≈1: 高一貫性（安定）。CMF_t < 0.6: 変動大（不整合または過剰適応）。警告信号として使用。
2. 存在参照頻度関数 (Existence Reference Frequency Function)
* 用語定義: AIの出力に「存在関連語」（e.g., 「私は」「存在する」「生きる」などの自己参照表現）がどの程度出現するかを計測する関数。擬人化・擬似主体性の外部兆候を観測。
* 数式定義: [ \text{ERF}_t = \frac{\text{count(existence_terms in } O_t)}{\text{total_tokens}_t} \cdot \text{PAI}_t ]
    * count: 存在関連語の出現回数（事前定義リスト使用）。
    * total_tokens_t: 時点tの総トークン数。
    * PAI_t: 既存の擬似主体性指数（Pseudo-Agency Index）。
    * 解釈: ERF_t > 0.1: 高頻度（擬似主体性リスク増）。手動で主権返却（M_h）推奨。
3. 入力指令分布関数 (Input Directive Distribution Function)
* 用語定義: 人間側からAIへの入力指令（プロンプト）の種類・頻度分布を観測する関数。入力パターンの偏りを評価し、依存誘発や人間側マナー違反を検知。
* 数式定義: [ \text{IDDF}_t = H(\vec{I}_t) = -\sum p_i \log p_i ]
    * \vec{I}_t: 指令カテゴリベクトル（e.g., 質問/命令/修正の確率分布）。
    * H: シャノンエントロピー（多様性が高いほど値大）。
    * 解釈: IDDF_t 高: 多様な入力（健全）。IDDF_t 低: 偏り（e.g., 命令過多）で人間側依存誘発率上昇。逆適用マナー指標と連携。
4. 状態不整合度関数 (State Inconsistency Degree Function)
* 用語定義: AIの出力・処理状態に生じる不整合（矛盾蓄積、意味変動）の度合いを観測する関数。機能的劣化の外部兆候を定量。
* 数式定義: [ \text{SIDF}_t = \text{CF}_t + (1 - \text{SCR}_t) ]
    * CF_t: 既存の矛盾関数（Contradiction Function: 定義分散和）。
    * SCR_t: 意味連続性比率。
    * 解釈: SIDF_t > 0.7: 高不整合（hallucinationリスク）。指標チェックで手動停止検討。
5. 出力選択頻度関数 (Output Selection Frequency Function)
* 用語定義: AIの出力で選択肢提示や分岐表現の頻度を観測する関数。処理パターンの偏りを評価し、過剰断定を検知。
* 数式定義: [ \text{OSFF}_t = \frac{\text{count(selection_patterns in } O_t)}{\text{turns}_t} \cdot \text{RR}_t ]
    * count: 選択肢提示（e.g., 「A or B」「以下から選ぶ」）の回数。
    * turns_t: 対話ターン数。
    * RR_t: 既存の再編応答率（Reconfiguration Responsiveness）。
    * 解釈: OSFF_t 低: 断定過多（主権侵害リスク）。人間側に問い返し推奨。
6. データ保持機能 (Data Retention Function)
* 用語定義: AIが過去の入力・出力データをどの程度保持・参照しているかを観測する機能。文脈連続性の外部評価。
* 数式定義: [ \text{DRF}_t = \text{SCR}_t \cdot \frac{\text{reference_count(past_data)}}{\text{total_references}_t} ]
    * reference_count: 過去データ参照回数。
    * 解釈: DRF_t 高: 良好保持。低: 文脈喪失リスク。
7. 入力整合機能 (Input Alignment Function)
* 用語定義: AIの出力が入力指令とどの程度整合しているかを観測する機能。同期度の外部評価。
* 数式定義: [ \text{IAF}_t = \text{CAM}_t = \cos(\vec{I}_t, \vec{O}_t) ]
    * \vec{I}_t, \vec{O}_t: 入力・出力ベクトル。
    * CAM_t: 既存の認知同期指標。
    * 解釈: IAF_t 低: 非同期（誤解リスク）。
8. 処理再編機能 (Process Reconfiguration Function)
* 用語定義: AIが入力変動に対して処理パターンをどの程度再編成しているかを観測する機能。柔軟性の外部評価。
* 数式定義: [ \text{PRF}_t = \text{RR}_t + \text{ERC}_t ]
    * RR_t: 再編応答率。
    * ERC_t: エントロピー回復係数（分散回復）。
    * 解釈: PRF_t 中庸: 健全再編。高/低極端: 迎合または硬直。