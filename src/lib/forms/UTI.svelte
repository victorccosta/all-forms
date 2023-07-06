<script lang="ts">
    import Repeatable from "../Repeatable.svelte";
    export let loading;
    
</script>

<mb-form>
    <div class="border shadow-lg p-5 rounded-lg flex flex-col gap-3 mt-5 md:p-10">

    <mb-date time path="imip-uti-tx.v0/context/document_entry_metadata/document_creation_time" label="Data"></mb-date>
    <mb-context path="imip-uti-tx.v0/context/start_time"></mb-context>
    <mb-context path="imip-uti-tx.v0/context/setting"></mb-context>
    

    <p class="font-bold text-lg">Alergias</p>
    <Repeatable let:i>

        <mb-input path="imip-uti-tx.v0/adverse_reaction_risk:${i}/substance" label="Substância"></mb-input>
        <mb-context path="imip-uti-tx.v0/adverse_reaction_risk:${i}/language"></mb-context>
        <mb-context path="imip-uti-tx.v0/adverse_reaction_risk:${i}/encoding"></mb-context>
        <mb-context path="imip-uti-tx.v0/adverse_reaction_risk:${i}/subject"></mb-context>
    </Repeatable>
        <mb-quantity default="kg" path="imip-uti-tx.v0/body_weight/weight" label="Peso">
            <mb-unit unit="kg" label="kg" min="" max="1000"></mb-unit>
        </mb-quantity>
        <mb-context path="imip-uti-tx.v0/body_weight/time"></mb-context>
        <mb-context path="imip-uti-tx.v0/body_weight/language"></mb-context>
        <mb-context path="imip-uti-tx.v0/body_weight/encoding"></mb-context>
        <mb-context path="imip-uti-tx.v0/body_weight/subject"></mb-context>
    
    </div>
    
    <div class="border shadow-lg p-5 rounded-lg flex flex-col gap-3 mt-5 md:p-10">
    <p class="font-bold text-lg">Hipoteses diagnosticas</p>
    <Repeatable let:i>

        <mb-input path="imip-uti-tx.v0/problem_diagnosis:${i}/problem_diagnosis_name" label="#{i+1}"></mb-input>
        <mb-context path="imip-uti-tx.v0/problem_diagnosis:${i}/language"></mb-context>
        <mb-context path="imip-uti-tx.v0/problem_diagnosis:${i}/encoding"></mb-context>
        <mb-context path="imip-uti-tx.v0/problem_diagnosis:${i}/subject"></mb-context>
    </Repeatable>
    </div>
    
    <div class="border shadow-lg p-5 rounded-lg flex flex-col gap-3 mt-5 md:p-10">
        <p class="font-bold text-lg">Dispositivos</p>
        <Repeatable let:i>
            <div class="border shadow-md rounded-lg flex flex-col gap-3 p-4">
                <mb-input path="imip-uti-tx.v0/physical_examination_findings/any_event:0/medical_device:${i}/device_name" label="Dispositivo"></mb-input>
                <mb-input path="imip-uti-tx.v0/physical_examination_findings/any_event:0/medical_device:${i}/anatomical_location/body_site_name" label="Local"></mb-input>
                <mb-date time path="imip-uti-tx.v0/physical_examination_findings/any_event:0/medical_device:${i}/date_of_insertion" label="Data de inserção"></mb-date>
            </div>
        </Repeatable>
        </div>

        <div class="border shadow-lg p-5 rounded-lg flex flex-col gap-3 mt-5 md:p-10">
            <p class="font-bold text-lg">Drogas em BIC</p>
            <Repeatable let:i>
                <div class="border shadow-md rounded-lg flex flex-col gap-3 p-4">
                    <mb-input path="imip-uti-tx.v0/physical_examination_findings/any_event:0/continuous_infusion_medications:${i}/name" label="Droga"></mb-input>
                    <mb-input  path="imip-uti-tx.v0/physical_examination_findings/any_event:0/continuous_infusion_medications:${i}/amount" label="Dose"></mb-input>
                    <mb-text-select path="imip-uti-tx.v0/physical_examination_findings/any_event:0/continuous_infusion_medications:${i}/amount_unit" label="Unidade">
                        <mb-option value="g/dia" label="g/dia"></mb-option>
                        <mb-option value="mg/kg/dia" label="mg/kg/dia"></mb-option>
                        <mb-option value="mL/h" label="mL/h"></mb-option>
                    </mb-text-select>
                </div>
                
    
            </Repeatable>
            </div>

    
    <mb-context path="imip-uti-tx.v0/physical_examination_findings/any_event:0/time"></mb-context>
    <mb-context path="imip-uti-tx.v0/physical_examination_findings/language"></mb-context>
    <mb-context path="imip-uti-tx.v0/physical_examination_findings/encoding"></mb-context>
    <mb-context path="imip-uti-tx.v0/physical_examination_findings/subject"></mb-context>
    <mb-quantity default="mL/min/1.73_m2" path="imip-uti-tx.v0/estimated_glomerular_filtration_rate_egfr/any_event:0/relative_egfr" label="Relative eGFR">
                    <mb-unit unit="mL/min/1.73_m2" label="mL/min/1.73_m2" min="" max=""></mb-unit>
                </mb-quantity>
    <mb-quantity default="ml/min" path="imip-uti-tx.v0/estimated_glomerular_filtration_rate_egfr/any_event:0/absolute_egfr" label="Absolute eGFR">
                    <mb-unit unit="ml/min" label="ml/min" min="" max=""></mb-unit>
                </mb-quantity>
    <mb-context path="imip-uti-tx.v0/estimated_glomerular_filtration_rate_egfr/any_event:0/time"></mb-context>
    <mb-select path="imip-uti-tx.v0/estimated_glomerular_filtration_rate_egfr/formula" label="Formula" terminology="local">
                <mb-option value="at0013" label="MDRD formula - non-IDMS-normalized serum Cr"></mb-option>
    <mb-option value="at0014" label="MDRD formula - IDMS-normalized serum Cr"></mb-option>
    <mb-option value="at0015" label="CKD-EPI Creatinine"></mb-option>
    <mb-option value="at0017" label="Bedside Schwartz equation"></mb-option>
    <mb-option value="at0016" label="Cockcroft-Gault formula"></mb-option>
    <mb-option value="at0021" label="LM Revised"></mb-option>
    <mb-option value="at0025" label="CKD-EPI Cystatin C"></mb-option>
    <mb-option value="at0026" label="CKD-EPI Creatinine-Cystatin C"></mb-option>
                </mb-select>
    <mb-input path="imip-uti-tx.v0/estimated_glomerular_filtration_rate_egfr/laboratory_analyte_result:0/analyte_name" label="Analyte name"></mb-input>
    <mb-select path="imip-uti-tx.v0/estimated_glomerular_filtration_rate_egfr/laboratory_analyte_result:0/analyte_result:0" label="Analyte result" terminology="undefined">
            </mb-select>
    <mb-context path="imip-uti-tx.v0/estimated_glomerular_filtration_rate_egfr/language"></mb-context>
    <mb-context path="imip-uti-tx.v0/estimated_glomerular_filtration_rate_egfr/encoding"></mb-context>
    <mb-context path="imip-uti-tx.v0/estimated_glomerular_filtration_rate_egfr/subject"></mb-context>
    <mb-input path="imip-uti-tx.v0/medication_statement/any_event:0/medication_item_name" label="Medication item name"></mb-input>
    <mb-date time path="imip-uti-tx.v0/medication_statement/any_event:0/first_prescribed" label="First prescribed"></mb-date>
    <mb-date time path="imip-uti-tx.v0/medication_statement/any_event:0/discontinued" label="Discontinued"></mb-date>
    <mb-context path="imip-uti-tx.v0/medication_statement/any_event:0/time"></mb-context>
    <mb-context path="imip-uti-tx.v0/medication_statement/language"></mb-context>
    <mb-context path="imip-uti-tx.v0/medication_statement/encoding"></mb-context>
    <mb-context path="imip-uti-tx.v0/medication_statement/subject"></mb-context>
    <mb-quantity default="ml" path="imip-uti-tx.v0/fluid_balance/any_interval_event:0/fluid_balance" label="Fluid balance">
                    <mb-unit unit="ml" label="ml" min="" max=""></mb-unit>
    <mb-unit unit="l" label="l" min="" max=""></mb-unit>
    <mb-unit unit="[foz_us]" label="[foz_us]" min="" max=""></mb-unit>
                </mb-quantity>
    <mb-duration year month hour path="imip-uti-tx.v0/fluid_balance/any_interval_event:0/width" label=""></mb-duration>
    <mb-context path="imip-uti-tx.v0/fluid_balance/any_interval_event:0/math_function"></mb-context>
    <mb-context path="imip-uti-tx.v0/fluid_balance/any_interval_event:0/time"></mb-context>
    <mb-context path="imip-uti-tx.v0/fluid_balance/language"></mb-context>
    <mb-context path="imip-uti-tx.v0/fluid_balance/encoding"></mb-context>
    <mb-context path="imip-uti-tx.v0/fluid_balance/subject"></mb-context>
    <mb-input path="imip-uti-tx.v0/fluid_output:0/any_event:0/fluid_name" label="Fluid name"></mb-input>
    <mb-quantity default="ml" path="imip-uti-tx.v0/fluid_output:0/any_event:0/volume" label="Volume">
                    <mb-unit unit="ml" label="ml" min="" max=""></mb-unit>
    <mb-unit unit="l" label="l" min="" max=""></mb-unit>
    <mb-unit unit="[foz_us]" label="[foz_us]" min="" max=""></mb-unit>
                </mb-quantity>
    <mb-context path="imip-uti-tx.v0/fluid_output:0/any_event:0/width"></mb-context>
    <mb-context path="imip-uti-tx.v0/fluid_output:0/any_event:0/math_function"></mb-context>
    <mb-context path="imip-uti-tx.v0/fluid_output:0/any_event:0/time"></mb-context>
    <mb-context path="imip-uti-tx.v0/fluid_output:0/language"></mb-context>
    <mb-context path="imip-uti-tx.v0/fluid_output:0/encoding"></mb-context>
    <mb-context path="imip-uti-tx.v0/fluid_output:0/subject"></mb-context>
    <mb-quantity default="Cel" path="imip-uti-tx.v0/body_temperature/any_event:0/temperature" label="Temperature">
                    <mb-unit unit="Cel" label="Cel" min="" max="100"></mb-unit>
                </mb-quantity>
    <mb-select path="imip-uti-tx.v0/body_temperature/any_event:0/math_function" label="" terminology="openehr">
                <mb-option value="144" label="maximum"></mb-option>
                </mb-select>
    <mb-duration year month hour path="imip-uti-tx.v0/body_temperature/any_event:0/width" label=""></mb-duration>
    <mb-context path="imip-uti-tx.v0/body_temperature/any_event:0/time"></mb-context>
    <mb-context path="imip-uti-tx.v0/body_temperature/language"></mb-context>
    <mb-context path="imip-uti-tx.v0/body_temperature/encoding"></mb-context>
    <mb-context path="imip-uti-tx.v0/body_temperature/subject"></mb-context>
    <mb-input path="imip-uti-tx.v0/faecal_output/any_event:0/comment" label="Comment"></mb-input>
    <mb-context path="imip-uti-tx.v0/faecal_output/any_event:0/width"></mb-context>
    <mb-context path="imip-uti-tx.v0/faecal_output/any_event:0/math_function"></mb-context>
    <mb-context path="imip-uti-tx.v0/faecal_output/any_event:0/time"></mb-context>
    <mb-context path="imip-uti-tx.v0/faecal_output/language"></mb-context>
    <mb-context path="imip-uti-tx.v0/faecal_output/encoding"></mb-context>
    <mb-context path="imip-uti-tx.v0/faecal_output/subject"></mb-context>
    <mb-input path="imip-uti-tx.v0/glicemia/any_event:0/test_name" label="Test name"></mb-input>
    <mb-input path="imip-uti-tx.v0/glicemia/any_event:0/conclusion" label="Conclusion"></mb-input>
    <mb-context path="imip-uti-tx.v0/glicemia/any_event:0/time"></mb-context>
    <mb-context path="imip-uti-tx.v0/glicemia/language"></mb-context>
    <mb-context path="imip-uti-tx.v0/glicemia/encoding"></mb-context>
    <mb-context path="imip-uti-tx.v0/glicemia/subject"></mb-context>

    <mb-input path="imip-uti-tx.v0/care_plan_request:0/activity/plan_name" label="Plan name"></mb-input>
    <mb-context path="imip-uti-tx.v0/care_plan_request:0/activity/timing"></mb-context>
    <mb-date time path="imip-uti-tx.v0/care_plan_request:0/expiry_time" label="expiry_time"></mb-date>
    <mb-context path="imip-uti-tx.v0/care_plan_request:0/narrative"></mb-context>
    <mb-context path="imip-uti-tx.v0/care_plan_request:0/language"></mb-context>
    <mb-context path="imip-uti-tx.v0/care_plan_request:0/encoding"></mb-context>
    <mb-context path="imip-uti-tx.v0/care_plan_request:0/subject"></mb-context>
    <mb-context path="imip-uti-tx.v0/category"></mb-context>
    <mb-context path="imip-uti-tx.v0/language"></mb-context>
    <mb-context path="imip-uti-tx.v0/territory"></mb-context>
    <mb-context path="imip-uti-tx.v0/composer"></mb-context>
    <mb-submit class="mt-4">
        <sl-button size="medium" class="mt-4 w-full" type="neutral" {loading}>
            Submit
        </sl-button>
    </mb-submit>
</mb-form>